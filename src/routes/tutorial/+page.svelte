<script>
  import SvelteMarkdown from "svelte-markdown";
  const source = `
  ### CROP-D can predict plant ailments in 3 simple steps:

#### 1. Head to the dashboard
<center>
	<img src="https://i.ibb.co/dkCvfSv/1.png" alt="1" border="0" height="300px"/>
</center>

#### 2. Upload an image of your ailing leaf and Hit TEST
<center><img src="https://i.ibb.co/JvcnMtH/2.png" alt="2" border="0" height="300px"></center>

#### 3. Get a diagnosis of the disease
<center><img src="https://i.ibb.co/X7hqD40/3.png" alt="3" border="0" height="300px"></center>

##### Additionally, you can learn more about the disease by hitting learn more

#### You can also learn more about the model by going to the [working](./working) page.
<center><img src="https://i.ibb.co/4MFxvBL/4.png" alt="4" border="0"></center>
`;
</script>

<head>
  <title>CROP-D|Tutorial</title>
</head>

<div class="wrapper">
  <div class="row">
    <div class="content-shell">Tutorial</div>
    <hr />
    <SvelteMarkdown {source} />
  </div>
</div>

<style>
  .wrapper,
  .row {
    margin: auto;display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }

  .wrapper {
    max-width: 1200px;
  }

  .row {
    width: 100%;
    margin-bottom: 10vh;
  }

  .content-shell {
    width: 100%;
    text-align: center;
    font-size: 2.5rem;
    font-weight: 800;
    color: var(--btn-primary-color-background-color);
  }
</style>
