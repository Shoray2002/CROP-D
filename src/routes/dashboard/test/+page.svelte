<script>
  // @ts-nocheck

  /**
   * @type {HTMLInputElement}
   */
  import Modal from "$lib/Modal.svelte";
  let diseaseObject = {
    Potato___healthy: "Potato Healthy",
    Potato___Late_blight: "Potato Late Blight",
    Potato___Early_blight: "Potato Early Blight",
    Tomato___healthy: "Tomato Healthy",
    Tomato___Late_blight: "Tomato Late Blight",
    Tomato___Early_blight: "Tomato Early Blight",
    Tomato___Leaf_Mold: "Tomato Leaf Mold",
    Tomato___Septoria_leaf_spot: "Tomato Septoria Leaf Spot",
    "Tomato___Spider_mites Two-spotted_spider_mite":
      "Tomato Two Spotted Spider Mite",
    Tomato___Target_Spot: "Tomato Target Spot",
    Tomato___Tomato_Yellow_Leaf_Curl_Virus: "Tomato Yellow Leaf Curl Virus",
    Tomato___Tomato_mosaic_virus: "Tomato Mosaic Virus",
    Tomato___Bacterial_spot: "Tomato Bacterial Spot",
    "Corn_(maize)___healthy": "Corn Healthy",
    "Corn_(maize)___Cercospora_leaf_spot Gray_leaf_spot": "Corn Gray Leaf Spot",
    "Corn_(maize)___Common_rust_": "Corn Common Rust",
    "Corn_(maize)___Northern_Leaf_Blight": "Corn Northern Leaf Blight",
    "Pepper,_bell___healthy": "Bell Pepper Healthy",
    "Pepper,_bell___Bacterial_spot": "Bell Pepper Bacterial Spot",
  };
  let showModal = false;
  let input;
  let card;
  let uploadLogo;
  let formdata;
  let identifiedPlant = "";
  let identifiedDisease = "";
  const upload = () => {
    input.click();
    input.addEventListener("change", (e) => {
      formdata = new FormData();
      const file = e.target.files[0];
      card.style.backgroundImage = `url(${URL.createObjectURL(file)})`;
      card.style.backgroundSize = "contain";
      card.style.backgroundPosition = "center";
      card.style.backgroundRepeat = "no-repeat";
      const img = new Image();
      img.src = URL.createObjectURL(file);
      img.onload = () => {
        const viewPortHeight = window.innerHeight;
        if (img.height < 0.6 * viewPortHeight) {
          card.style.height = `${img.height + 100}px`;
        } else {
          card.style.height = `${0.6 * viewPortHeight}px`;
        }
        const aspectRatio = img.width / img.height;
        card.style.width = card.style.height * aspectRatio + "px";
        uploadLogo.style.filter = "invert(0.9)";
      };
      formdata.append("image", file, file.name);
    });
  };
  const rdirect = () => {
    window.open(
      "https://www.planetnatural.com/?s=" +
        identifiedPlant +
        " " +
        identifiedDisease
    );
  };

  const test = () => {
    fetch("https://autochaptering.pagekite.me/upload", {
      method: "POST",
      body: formdata,
      redirect: "follow",
    })
      .then((response) => response.text())
      .then((result) => {
        showModal = true;
        result = diseaseObject[result];
        if (result) {
          result = result.split(" ");
          identifiedPlant = result[0];
          identifiedDisease = result.slice(1).join(" ");
        } else {
          identifiedPlant = "Plant";
          identifiedDisease = "no";
        }
      })
      .catch((error) => console.log("error", error));
  };
</script>

<head>
  <title>CROP-D|DashBoard</title>
</head>
<div class="wrapper">
  <div class="row">
    <div class="content-shell">
      <div class="card card-100" on:click={() => upload()} bind:this={card}>
        <h3>Drag-Or-Drop <br />your <br /> Image here</h3>
        <div class="upload-icon">
          <img
            src="https://img.icons8.com/ios/512/upload.png"
            alt="upload"
            bind:this={uploadLogo}
          />
        </div>
        <input type="file" accept="image/*" bind:this={input} />
      </div>
      <div class="btn btn-primary" on:click={() => test()}>TEST</div>
    </div>
  </div>
  {#if showModal}
    <Modal on:close={() => (showModal = false)}>
      <div slot="header" class="header-div">
        {#if identifiedDisease == "no" || identifiedPlant == "Plant"}
          <h2 class="modal-header">
            <span class="heading-prefix">No Disease Found </span>
          </h2>
        {:else}
          <h2 class="modal-header">
            <span class="heading-prefix"> Predicted Crop and Disease: </span>
            <br />
            <span class="heading-suffix">
              <a
                href={"https://www.google.co.in/search?q=" +
                  identifiedPlant +
                  " " +
                  identifiedDisease}
                style="cursor:pointer; text-decoration:none;"
                target="_blank"
              >
                <em>{identifiedPlant} - {identifiedDisease} </em></a
              >
            </span>
          </h2>
          <hr />
          <div class="btn btn-primary" on:click={() => rdirect()}>
            Learn More...
          </div>
        {/if}
      </div>
    </Modal>
  {/if}
</div>

<style>
  .modal-header {
    font-size: 2rem;
    font-weight: 500;
    margin-top: 0.3rem;
    text-align: center;
    font-weight: 800;
  }
  .header-div {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }
  .wrapper,
  .row {
    margin: auto;
  }

  .wrapper {
    max-width: 1200px;
  }

  .row {
    width: 100%;
  }

  .content-shell {
    margin-top: 40px;
    width: 100%;
    height: 50vh;
    display: flex;
    align-items: center;
    text-align: center;
    justify-content: center;
    flex-direction: column;
  }

  .content-shell .card {
    align-self: stretch;
  }
  .content-shell .content-shell .card {
    height: 25vh;
  }

  .card {
    border: #000000 dashed 3px;
    position: relative;
    color: #ededed;
    width: 100%;
    margin: 0.5em 0.3em;
    border-radius: 0.5em;
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    padding-bottom: 20px;
  }

  h3 {
    margin-bottom: 0;
    font-family: "Titillium Web", sans-serif;
    color: whitesmoke;
    filter: drop-shadow(0 0 0.09rem #000000);
    font-weight: 800;
  }
  .card:hover {
    cursor: pointer;
  }

  .card:hover:after {
    opacity: 0.08;
  }

  .card:before,
  .card:after {
    display: block;
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    transition: opacity 0.4s cubic-bezier(0.075, 0.82, 0.165, 1);
    pointer-events: none;
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
  }

  .card:after {
    background: #121212;
    opacity: 0;
    z-index: -1;
  }

  .upload-icon img {
    height: 8rem;
  }
  input {
    display: none;
  }

  iframe {
    width: inherit;
    height: 70vh;
  }

  .heading-prefix {
    font-weight: 800;
    color: var(--btn-primary-color-background-color);
  }
  .heading-suffix {
    font-weight: 400;

    text-transform: capitalize;
  }
</style>
