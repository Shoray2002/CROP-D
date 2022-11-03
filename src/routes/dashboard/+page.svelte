<script>
  // @ts-nocheck

  import Modal from "$lib/Modal.svelte";
  let showModal = false;
</script>

<head>
  <title>CROP-D|DashBoard</title>
</head>

<div class="wrapper">
  <div class="row">
    <div class="content-shell">
      <div class="card card-100">
        <div class="card-content">
          <div class="top-content">
            <h3 class="card-heading">Test a leaf</h3>
            <div class="card-icon" on:click={() => (showModal = true)}>
              <svg
                xmlns="http://www.w3.org/2000/svg"
                width="40"
                height="40"
                viewBox="0 1 22 22"
                fill="none"
                stroke="currentColor"
                stroke-width="1"
                class="feather feather-settings"
              >
                <path
                  stroke="currentColor"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M14 21h-4l-.551-2.48a6.991 6.991 0 0 1-1.819-1.05l-2.424.763-2-3.464 1.872-1.718a7.055 7.055 0 0 1 0-2.1L3.206 9.232l2-3.464 2.424.763A6.992 6.992 0 0 1 9.45 5.48L10 3h4l.551 2.48a6.992 6.992 0 0 1 1.819 1.05l2.424-.763 2 3.464-1.872 1.718a7.05 7.05 0 0 1 0 2.1l1.872 1.718-2 3.464-2.424-.763a6.99 6.99 0 0 1-1.819 1.052L14 21z"
                /><circle
                  cx="12"
                  cy="12"
                  r="3"
                  stroke="currentColor"
                  stroke-width="2"
                />
              </svg>
            </div>
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
        <div class="card-bgimg" />
      </div>
      {#if showModal}
        <Modal on:close={() => (showModal = false)}>
          <h2 slot="header">Select a Model</h2>
          <!-- radio -->
          <div class="radio">
            <input
              type="radio"
              id="radio-1"
              name="radio"
              value="radio-1"
              checked
            />
            <label for="radio-1"
              >Random Forest Classifier <a href="/">learn more</a>
            </label>
          </div>
          <div class="radio">
            <input type="radio" id="radio-2" name="radio" value="radio-2" />
            <label for="radio-2"
              >ResNet Classifier <a href="/">learn more</a></label
            >
          </div>

          <!-- <ol class="definition-list">
            <li>of or relating to modality in logic</li>
            <li>
              containing provisions as to the mode of procedure or the manner of
              taking effect —used of a contract or legacy
            </li>
            <li>of or relating to a musical mode</li>
            <li>of or relating to structure as opposed to substance</li>
            <li>
              of, relating to, or constituting a grammatical form or category
              characteristically indicating predication
            </li>
            <li>of or relating to a statistical mode</li>
          </ol> -->
        </Modal>
      {/if}
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
    border: 2px solid #ededed;
    padding: 1em 1.5em;
    font-family: "Titillium Web", sans-serif;
    border-radius: 0.5rem;
  }

  .card {
    position: relative;
    color: #ededed;
    width: 100%;
    overflow: hidden;
    margin: 0.5em 0.3em;
    border-radius: 0.5em;
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

  .card-bgimg {
    background-color: aquamarine;
    background: url(https://soybeanresearchinfo.com/wp-content/uploads/2020/05/Frogeye-leaf-spot-Daren-Mueller-16-1300x867.jpg)
      no-repeat center center;
  }

  .card:hover .card-bgimg {
    transform: scale(1.2) translateX(5%);
  }

  .card:hover .card-action {
    opacity: 1;
    transform: translate(-50%, 0);
  }

  .top-content {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .card-icon {
    animation: spin 2s linear infinite;
    filter: drop-shadow(0 0 0.5rem #000000);
  }
  .card-icon:hover {
    scale: 1.1;
    color: blanchedalmond;
    animation: none;
  }

  @keyframes spin {
    0% {
      transform: rotate(0deg);
    }
    100% {
      transform: rotate(360deg);
    }
  }

  /* .card-100 .card-content {
    transform: translateY(75.5%);
  } */

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

  .card-heading {
    font-size: 3.2em;
    font-weight: 400;
    color: var(--dashboard-heading-color-1);
    margin: 0;
    filter: drop-shadow(0px 3px 3px black);
  }
  .card-body p {
    font-size: 1.2rem;
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
