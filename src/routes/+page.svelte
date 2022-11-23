<script>
  import crop_logo from "$lib/assets/crop.svg";
</script>

<head>
  <title>CROP-D|Home</title>
</head>
<!-- banner -->
<div class="content-section-container text-centered bp-100 hero-section">
  <img src={crop_logo} alt="CROP-D" class="hero-img" />
  <div class="hero-text">
    <h1>
      Classification and Recognition Of <span class="header-bold"
        >Plant Diseases</span
      >
    </h1>
    <p />
    <a class="btn btn-primary" href="/dashboard">DashBoard</a>
  </div>
</div>

<!-- features -->

<div class="bp-80" />
<div class="outer-container features">
  <div class="simple-flex">
    <div class="content-section-container border-bottom benefits-container">
      <h2 class="desktop-only bm-40">
        Features of <span class="header-bold">C.R.O.P-D</span>
      </h2>
    </div>
    <div class="panels-img-container">
      <h2 class="mobile-only bm-40">
        Features of <span class="header-bold">C.R.O.P-D</span>
      </h2>

      <div class="panels">
        <div class="panel panel-blue">
          <h5 class="header-bold">Support for Common Crops</h5>
          <p>
            CROP-D supports the most common crops in India like Potato, Tomato,
            Bell Pepper and Corn. We are working on adding more crops to the
            list.
          </p>
        </div>
        <div class="panel panel-purple">
          <h5 class="header-bold">Reliable Model</h5>
          <p>
            CROP-D uses advanced ResNet model trained on thousands of samples to
            provide the best results.
          </p>
        </div>
        <div class="panel panel-purple">
          <h5 class="header-bold">Quick and Portable</h5>
          <p>
            CROP-D is a web application that can be used on any device with an
            internet connection. You can use it on your phone, tablet or laptop.
          </p>
        </div>

        <div class="panel panel-blue">
          <h5 class="header-bold">Learn More</h5>
          <p>
            CROP-D provides easy access to additional information on how to cure the
            identified disease.
          </p>
        </div>
      </div>
    </div>
  </div>
  <div class="bp-80" />
  <!-- 
  <footer class="content-section-container text-centered">
    <h3>
      <span class="header-bold">CVisor</span> is a project by
      <a class="website" href="https://lordshoray.is-a.dev/" target="_blank"
        >Shoray Singhal</a
      >
    </h3>
    <h5 class="rm-20 header-bold">Found a Bug? Report @</h5>
    <h5 class="bm-15" style="color:#5c5fb8;">shoryasinghall@gmail.com</h5>
  </footer> -->
</div>

<style>
  .hero-img {
    animation: rotate 10s linear infinite alternate;
  }

  @keyframes rotate {
    from {
      transform: rotate(-10deg);
      filter: hue-rotate(-30deg);
    }
    to {
      transform: rotate(10deg);
      filter: hue-rotate(30deg);
    }
  }
  .features {
    padding: 2rem;
  }
  @media only screen and (min-width: 992px) {
    .features {
      padding: 0rem;
    }
  }
</style>
