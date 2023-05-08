<script>
  import { Page,Navbar, List, ListInput, ListItem, Toggle, BlockTitle, Button, Range, Block, useStore, Preloader, BlockHeader, TextEditor } from 'framework7-svelte';
  import Editor from '../components/editor.svelte';

  import store from '../js/store';
	// import { marked } from 'marked';
	
  const userContext = {
    current: '',
    revision: '',
    changes: '',
  }

  let isLoading = false;


  const recordChanges = (value) => {
    userContext.current = value;
  }


  const getSuggestions = () => {
    postJSON({user_input: userContext.current});    
  }


  const acceptSuggestions = () => {
    userContext.current = userContext.revision;
    userContext.changes = '';
    userContext.revision = '';
  }


  async function postJSON(data) {
    try {
      if (isLoading) return;
      isLoading = true;

      fetch("https://e1eqlo3j7c.execute-api.us-east-1.amazonaws.com/alpha/copyedit", {
        method: "POST",
        // headers: {
        //   "Content-Type": "application/json",
        // },
        mode: 'cors',
        body: JSON.stringify(data),
      })
      .then((response) => response.text())
      .then((result) => {
        var [revision, changes] = result.split('----------')
        console.log('revision',revision);
        console.log('changes',changes);
        userContext.revision = revision;
        userContext.changes = `<strong>Changes:</strong>${changes}`;
        isLoading = false
      });
    } 
    catch (error) {
      console.error("Error:", error);
    }
  }

</script>



<Page name="form">
  <BlockTitle>CopyEditApp</BlockTitle>



  <List strongIos outlineIos dividersIos>

    <BlockHeader>You can write anything you want to copy edit.</BlockHeader>

    <TextEditor
      value={userContext.current}
      onTextEditorChange={(value) => (userContext.current = value)}
      buttons={[[]]}
    />


    <Block>
      <Button fill preloader loading={isLoading} onClick={getSuggestions}>Suggest Changes</Button>
    </Block>



    <Editor
      value={userContext.revision}
    />


    <Block>
      <pre>
        {@html userContext.changes}
      </pre>
    </Block>



    <Block>
      <Button fill onClick={acceptSuggestions}>Accept Changes</Button>
    </Block>





  </List>
  
</Page>
