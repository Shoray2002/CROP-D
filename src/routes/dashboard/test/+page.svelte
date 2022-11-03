<script>
  // @ts-nocheck

  /**
   * @type {HTMLInputElement}
   */
  let input;
  const upload = () => {
    input.click();
  };
  let handleDragDrop = (
    /** @type {{ preventDefault: () => void; stopPropagation: () => void; dataTransfer: { files: any; }; }} */ e
  ) => {
    console.log("dropped");
  };
</script>

<head>
  <title>CROP-D|DashBoard</title>
</head>
<div class="wrapper">
  <div class="row">
    <div class="content-shell">
      <div
        class="card card-100"
        on:click={() => upload()}
      >
        <h3>Drag-Or-Drop <br />your <br /> Image here</h3>
        <div class="upload-icon">
          <img src="https://img.icons8.com/ios/512/upload.png" alt="upload" />
        </div>
        <input type="file" accept="image/png" bind:this={input} />
      </div>
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
    width: 100%;
    height: 50vh;
    display: flex;
    align-items: center;
    text-align: center;
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
