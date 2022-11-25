<script>
  // @ts-nocheck
  import SvelteMarkdown from "svelte-markdown";

  const rdirect = () => {
    window.open("https://towardsdatascience.com/stacking-classifiers-for-higher-predictive-performance-566f963e4840");
  };  
  const source = `
  <img src="https://miro.medium.com/max/665/1*0hEXoK6zXhTt05q3V3vmnA.png" alt="s" border="0">

  #### This ML model consists of a stacking classifier(ensemble learning method) that uses the features obtained after  feature extractionfrom the image and feature selection to select the most relevant features. The model uses the following classifiers: Random Forest Classifier, K Nearest Neighbours, and Classifier Tree.
  ##### The achieved accuracy on the test dataset was 95.4%

### The prediction workflow is like this:

#### 1. The user uploads an image of a leaf belonging to the diseased plant

#### 2. The uploaded image is first temporarily stored in a folder named "uploads"

#### 3. Feature Extraction happens on the uploaded image 
| Feature      | Description | Link     |
| :---        |    :----   |          ---: |
| Hu Momement      | Weighted average of image pixel intensities | [Hu Moment](https://learnopencv.com/shape-matching-using-hu-moments-c-python/)   |
|Haralick Texture   | Haralick's paper describes applying the 14 equations above to four angular gray-Level co-occurrence spatial dependency matrices, which results in four values from each equation above. Haralick computed the mean and range for each of the 14 sets of four values resulting in 28 features.  | [HT](https://earlglynn.github.io/RNotes/package/EBImage/Haralick-Textural-Features.html)      |
|Color Histogram   | Color histogram is a representation of the distribution of colors in an image        | [CH](https://en.wikipedia.org/wiki/Color_histogram )     |

#### 4. Then Feature selection happens on the extracted features. We reduce the input variable to our model by using only relevant data and getting rid of noise.


#### 5. Then we cross validate the selected features to evaluate various models. We then use the ensemble technique to combine the predictions of the models to get the final prediction.

#### 6. We then produce the final prediction and display it to the user.

##### Given below are relvant figures of the training process:

<a href="https://imgbb.com/"><img src="https://i.ibb.co/263Vzkm/photo-2022-11-25-15-11-20.jpg" alt="cm" border="0"></a>
<a href="https://imgbb.com/"><img src="https://i.ibb.co/BB8KQXV/models-2.png" alt="models" border="0"></a>
<a href="https://imgbb.com/"><img src="https://i.ibb.co/4dxhvkf/output1.png" alt="output1" border="0"></a>
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
