<script>
</script>

<head>
  <title>CROP-D|DashBoard</title>
</head>

<div class="wrapper">
  <div class="row">
    <div class="content-shell">
      <div class="card card-100">
        <div class="card-content">
          <div class="card-heading">
            <h3>Test a leaf</h3>
          </div>
          <div class="card-body">
            <p>Upload an image of a leaf to test for disease.</p>
          </div>
        </div>
        <div
          class="card-action"
          on:click={() => {
            window.location.href = "/dashboard/test";
          }}
        >
          <button>Get Started</button>
        </div>
        <div class="card-bgimg" style="background:whitesmoke;" />
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
    align-items: flex-start;
  }

  .content-shell .card {
    align-self: stretch;
  }

  .content-shell .content-shell .card {
    height: 25vh;
  }

  button {
    -webkit-appearance: none;
    -moz-appearance: none;
    appearance: none;
    background: none;
    color: #ededed;
    border: 1px solid #ededed;
    padding: 1em 1.5em;
    font-family: "Titillium Web", sans-serif;
  }

  .card {
    position: relative;
    color: #ededed;
    width: 100%;
    overflow: hidden;
    margin: 0.5em;
  }

  .card:hover {
    cursor: pointer;
  }

  .card:hover:after {
    opacity: 0.5;
  }

  .card:hover:before {
    transform: scale(0.925, 0.925);
    opacity: 1;
  }

  .card:hover p {
    opacity: 1;
  }

  .card:hover .card-content {
    transform: translateY(0);
  }

  .card:hover .card-bgimg {
    transform: scale(1.1);
  }

  .card:hover .card-action {
    opacity: 1;
    transform: translate(-50%, 0);
  }

  .card-100 .card-content {
    transform: translateY(75.5%);
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

  /* .card:before {
    opacity: 0;
    border: 1px solid #ededed;
    transform-origin: center center;
    transition: transform 0.3s cubic-bezier(0.075, 0.82, 0.165, 1),
      opacity 0.4s cubic-bezier(0.075, 0.82, 0.165, 1);
  } */

  .card:after {
    background: #121212;
    opacity: 0;
    z-index: -1;
  }

  .card-content,
  .card-action {
    position: absolute;
  }

  .card-content {
    top: 2em;
    left: 2em;
    right: 2em;
    height: 100%;
    transition: transform 0.5s cubic-bezier(0.075, 0.82, 0.165, 1);
    transform: translateY(65%);
  }

  .card-action {
    position: absolute;
    bottom: 2em;
    left: 50%;
    transform: translate(-50%, 100%);
    opacity: 0;
    pointer-events: all;
    transition: opacity 0.75s cubic-bezier(0.075, 0.82, 0.165, 1),
      transform 0.6s cubic-bezier(0.075, 0.82, 0.165, 1);
  }

  /* .card-action:hover{ */

  .card h3 {
    margin-top: 0;
  }

  .card p {
    opacity: 0;
    transition: opacity 1.4s cubic-bezier(0.075, 0.82, 0.165, 1);
  }

  .card-bgimg {
    position: absolute;
    z-index: -1;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    transition: transform 0.6s cubic-bezier(0.075, 0.82, 0.165, 1);
    transform: scale(1);
    background-size: cover;
    background-position: center center;
    background-repeat: no-repeat;
  }

  @media (min-width: 768px) {
    .inner {
      width: 80%;
    }
  }
</style>
