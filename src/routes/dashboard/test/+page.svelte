<script>
  // @ts-nocheck

  /**
   * @type {HTMLInputElement}
   */
  let input;
  let card;
  let uploadLogo;
  const upload = () => {
    input.click();
    input.addEventListener("change", (e) => {
      const file = e.target.files[0];
      console.log(URL.createObjectURL(file));
      card.style.backgroundImage = `url(${URL.createObjectURL(file)})`;
      card.style.backgroundSize = "contain";
      card.style.backgroundPosition = "center";
      card.style.backgroundRepeat = "no-repeat";
      const img = new Image();
      img.src = URL.createObjectURL(file);
      img.onload = () => {
        // get viewport size
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
    });
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
      <a class="btn btn-primary" href="/upload">TEST</a>
    </div>
  </div>
</div>

<style>
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
</style>
