<script>
  // @ts-nocheck

  /**
   * @type {HTMLInputElement}
   */
  import Modal from "$lib/Modal.svelte";
  let showModal = false;
  let input;
  let card;
  let uploadLogo;
  let formdata;
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
      formdata.append("file", file, file.name);
    });
  };

  const test = () => {
    console.log("early blight");
    showModal = true;
    identifiedDisease = "early blight";
  };

  const rdirect = () => {
    window.open("https://www.planetnatural.com/?s=" + identifiedDisease);
  };

  // const test = () => {
  //   fetch("https://autochaptering.pagekite.me/upload", {
  //     method: "POST",
  //     body: formdata,
  //     redirect: "follow",
  //   })
  //     .then((response) => response.text())
  //     .then((result) => console.log(result))
  //     .catch((error) => console.log("error", error));
  // };
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
      <h2 slot="header" class="modal-header">
        <span class="heading-prefix"> Predicted Disease and Crop: </span> <br />
        <span class="heading-suffix">
          <a
            href={"https://www.google.co.in/search?q=" + identifiedDisease}
            style="cursor:pointer; text-decoration:none;"
            target="_blank"
          >
            <em> {identifiedDisease} </em></a
          ></span
        >
      </h2>
      <hr />
      <div class="btn btn-primary" on:click={() => rdirect()}>
        Learn More...
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
