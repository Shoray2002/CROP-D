<script>
  // @ts-nocheck
  import SvelteMarkdown from "svelte-markdown";

  const rdirect = () => {
    window.open("https://en.wikipedia.org/wiki/Residual_neural_network");
  };
  const source = `
  <img src="https://i.ibb.co/ThpC42t/s.png" alt="s" border="0">

  #### In ResNets, unlike in traditional neural networks, each layer feeds into the next layer, we use a network with residual blocks, each layer feeds into the next layer and directly into the layers about 2–3 hops away, to avoid over-fitting (a situation when validation loss stop decreasing at a point and then keeps increasing while training loss still decreases). This also helps in preventing vanishing gradient problem and allow us to train deep neural networks. Here is a simple residual block. We trained ResNet9 model with 6,589,734 parameters for this task.
  ##### The achieved accuracy on the test dataset was 99.2%

  ### The prediction workflow is like this:

#### 1. The user uploads an image of a leaf belonging to the diseased plant

#### 2. The uploaded image is first temporarily stored in a folder named "uploads"

#### 3. The prediction is carried out by creating a new instance of the ResNet model and loading the trained model (all its weights and biases) into it

#### 4. The image is then preprocessed (its converted into a tensor, and then normalized) and the disease is then predicted using the model

#### 5. These results are then displayed to the user, along with a link to the page containing the details of the disease

##### Learn More about Resnet below
`;
</script>

<head>
  <title>CROP-D|Working</title>
</head>

<div class="wrapper">
  <div class="row">
    <div class="content-shell">Working</div>
    <hr />
    <SvelteMarkdown {source} />
    <div class="btn btn-primary" on:click={() => rdirect()}>Learn More...</div>
  </div>
</div>

<style>
  .wrapper,
  .row {
    margin: auto;
    display: flex;
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
