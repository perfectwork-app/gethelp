---
title: Getting Started
no_toc: true
---

<!-- Custom HTML site displayed as the Home chapter -->


<style>

    .md-main {
        flex-grow: 0
    }

    .md-main__inner {
        display: flex;
        height: 100%;
    }

    .tx-container {
        padding-top: .0rem;
        background: linear-gradient(to bottom, var(--md-primary-fg-color), hsla(160deg,47%,55%,1) 99%,#fff 99%)
    }

    .tx-hero {
        margin: 32px 2.8rem;
        color: var(--md-primary-bg-color);
        justify-content: center;
    }

    .tx-hero h1 {
        margin-bottom: 1rem;
        color: currentColor;
        font-weight: 700;
        margin: 0 auto;
    }

    .tx-hero__content {
        padding-bottom: 1rem;
        margin: 0 auto;
    }

    .tx-hero__image{
        width:17rem;
        height:17rem;
        order:1;
        padding-right: 2.5rem;
    }

    .tx-hero .md-button {
        margin-top: .5rem;
        margin-right: .5rem;
        color: var(--md-primary-bg-color)
    }

    .tx-hero .md-button--primary {
        background-color: var(--md-primary-bg-color);
        color: hsla(280deg, 37%, 48%, 1);
        border-color: var(--md-primary-bg-color)
    }

    .tx-hero .md-button:focus,
    .tx-hero .md-button:hover {
        background-color: var(--md-accent-fg-color);
        color: var(--md-default-bg-color);
        border-color: var(--md-accent-fg-color)
    }

    .feature-item h2 svg {
        height: 30px;
        float: left;
        margin-right: 10px;
        transform: translateY(10%);
    }

    .top-hr {
        margin-top: 42px;
    }

    .feature-item {
        font-family: 'Lato', sans-serif;
        font-weight: 300;
        box-sizing: border-box;
        padding: 0 15px;
        word-break: break-word
    }

    .feature-item h2 {
        color: #333;
        font-weight: 300;
        font-size: 25px;
        white-space: nowrap;
        overflow: hidden;
        text-overflow: ellipsis;
        line-height: normal;
        margin-top: 20px;
        margin-bottom: 10px;
        font-family: inherit;
    }

    .feature-item p {
        font-size: 16px;
        line-height: 1.8em;
        text-rendering: optimizeLegibility;
        -webkit-font-smoothing: antialiased;
        color: #111;
        margin: 0 0 10px;
        display: block;
    }

    @media screen and (max-width:30em) {
        .tx-hero h1 {
            font-size: 1.4rem
        }
    }

    @media screen and (min-width:60em) {
        .md-sidebar--secondary {
            display: none
        }

        .tx-hero {
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .tx-hero__content {
            max-width: 22rem;
            margin-top: 3.5rem;
            margin-bottom: 3.5rem;
            margin-left: 1.0rem;
            margin-right: 4.0rem;
            align-items: center;
        }
    }

    @media screen and (min-width:76.25em) {
        .md-sidebar--primary {
            display: none
        }

        .top-hr {
            width: 100%;
            display: flex;
            max-width: 61rem;
            margin-right: auto;
            margin-left: auto;
            padding: 0 .2rem;
        }

        .bottom-hr {
            margin-top: 10px;
            width: 100%;
            display: flex;
            max-width: 61rem;
            margin-right: auto;
            margin-left: auto;
            padding: 0 .2rem;
        }

        .feature-item {
            flex: 1;
            min-width: 0;
        }

        .feature-item:hover {
            background-color: #526cfe47;
            border-radius: 3px;
        }
    }

    .hr {
        border-bottom: 1px solid #eee;
        width: 100%;
        margin: 20px 0;
    }

    .text-center {
        text-align: center;
        padding-right: 15px;
        padding-left: 15px;
        margin-right: auto;
        margin-left: auto;
        margin-top: 15px;
        font-family: 'Lato', sans-serif;
        font-size: 23px;
        font-weight: 300;
        padding-bottom: 10px;
    }

    .logos {
        display: flex;
        align-items: center;
        justify-content: center;
        flex-flow: row wrap;
        margin: 0 auto;
    }

    .logos img {
        flex: 1 1 auto;
        padding: 25px;
        max-height: 130px;
        vertical-align: middle;
    }

    .hr-logos {
        margin-top: 0;
        margin-bottom: 30px;
    }

    .md-footer-meta__inner {
        display: flex;
        flex-wrap: wrap;
        justify-content: space-between;
        margin-top: 1.0rem;
    }

    .md-footer-social {
        padding-top: 20px;
    }
</style>

<!-- Main site Entry button descriptions -->
<section>
  <div class="container px-5 py-24 mx-auto flex flex-wrap">
    <h1 class="sm:text-3xl text-2xl text-red-900 font-medium mb-2 md:w-2/5">PerfectWORK Business Solutions<br/><p class="text-xl italic text-gray-700 font-medium">Perfecting Your Business Decision
    </p></h1>
    <div class="md:w-3/5 md:pl-6">
      <p class="leading-relaxed text-base">The next generation business information system, which helps you to grow your business , with powerful modular design covering all essential aspects of a business. It is better now</p>
      <div class="flex md:mt-4 mt-6">
        <a href="/01_user_guide"><button class="inline-flex text-white bg-green-500 border-0 py-1 px-4 focus:outline-none hover:bg-green-600 rounded">Documentation</button></a>
        <a href="https://perfectwork.app" class="text-green-500 inline-flex items-center ml-4">Learn More
          <svg fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" class="w-4 h-4 ml-2" viewBox="0 0 24 24">
          </svg>
        </a>
      </div>
    </div>
  </div>
</section>

<!-- This example requires Tailwind CSS v2.0+ -->
<div class="relative bg-white overflow-hidden">
 <div class="p-10 grid grid-cols-1 sm:grid-cols-1 md:grid-cols-3 lg:grid-cols-3 xl:grid-cols-3 gap-5">
    <!--Card 1-->
    <a href="/gethelp/01_user_guide" class="rounded overflow-hidden shadow-lg">
      <img class="w-full" src="./assets/images/platform.jpg" alt="Platform">
      <div class="px-6 py-4">
        <div class="font-bold text-xl mb-2">PerfectWORK Platform</div>
        <p class="text-gray-700 text-sm font-light">
          PerfectWORK is the next generation business management system, which helps you to accelerate the growth of your business.
        </p>
      </div>
    </a>
    <!--Card 2-->
    <div class="rounded overflow-hidden shadow-lg">
      <img class="w-full" src="./assets/images/accounting.jpg" alt="Accounting and Finance" >
      <div class="px-6 py-4">
        <div class="font-bold text-xl mb-2">Finance & Accounting</div>
        <p class="text-gray-700 text-sm font-light">
           An Easy to Use Accounting System to keep track of organizational Expenses, Receivables and Payables with All Good Practices built-in
        </p>
      </div>
    </div>
    <!--Card 3-->
    <div class="rounded overflow-hidden shadow-lg">
      <img class="w-full" src="./assets/images/sales.jpg" alt="Forest">
      <div class="px-6 py-4">
        <div class="font-bold text-xl mb-2">Sales & Distribution</div>
        <p class="text-gray-700 text-sm font-light">
          Unlock Tremendous Sales Opportunities with a Robust Sales Force Automation
        </p>
      </div>
    </div>
    <!--Card 4 -->
    <!-- <div class="rounded overflow-hidden shadow-lg">
      <img class="w-full" src="/forest.jpg" alt="Forest">
      <div class="px-6 py-4">
        <div class="font-bold text-xl mb-2">Forest</div>
        <p class="text-gray-700 text-base">
          Lorem ipsum dolor sit amet, consectetur adipisicing elit. Voluptatibus quia, Nonea! Maiores et perferendis eaque, exercitationem praesentium nihil.
        </p>
      </div>
      <div class="px-6 pt-4 pb-2">
        <span class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2">#photography</span>
        <span class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2">#travel</span>
        <span class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2">#fall</span>
      </div>
    </div> -->
    </div>
  </div>
</div>

</div>


<section class="text-gray-600 body-font relative">
  <div class="absolute inset-0 bg-gray-300">
    <iframe width="100%" height="100%" frameborder="0" marginheight="0" marginwidth="0" title="map" scrolling="no" src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3988.738488314965!2d103.8996264149317!3d1.3330577620000716!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x31da1720a1f05045%3A0x76e9f3c4951e6836!2sSyner-Catalyst%20Pte%20Ltd!5e0!3m2!1sen!2ssg!4v1638951186433!5m2!1sen!2ssg" style="filter: grayscale(1) contrast(1.2) opacity(0.4);"></iframe>
  </div>
  <div class="container px-5 py-24 mx-auto flex">
    <div class="lg:w-1/3 md:w-1/2 bg-white rounded-lg p-8 flex flex-col md:ml-auto w-full mt-10 md:mt-0 relative z-10 shadow-md">
      <h2 class="text-gray-900 text-lg mb-1 font-medium title-font">Talk to Us</h2>
      <p class="leading-relaxed mb-5 text-gray-700">We can be your business partner</p>
      <div class="relative mb-4">
        <label for="email" class="leading-7 text-sm text-gray-600">Email</label>
        <input type="email" id="email" name="email" class="w-full bg-white rounded border border-gray-500 focus:border-indigo-500 focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out">
      </div>
      <div class="relative mb-4">
        <label for="message" class="leading-7 text-sm text-gray-600">Message</label>
        <textarea id="message" name="message" class="w-full bg-white rounded border border-gray-300 focus:border-indigo-500 focus:ring-2 focus:ring-indigo-200 h-32 text-base outline-none text-gray-700 py-1 px-3 resize-none leading-6 transition-colors duration-200 ease-in-out"></textarea>
      </div>
      <button class="text-white bg-indigo-500 border-0 py-2 px-6 focus:outline-none hover:bg-green-600 rounded text-lg">Contact Us</button>
      <p class="text-xs text-gray-500 mt-3">Looking forwards to work with you</p>
    </div>
  </div>
</section>

<!-- Custom narrow footer -->
<div class="md-footer-meta__inner md-grid">
    <div class="md-footer-social">
    <a class="md-footer-social__link" href="https://github.com/up42" rel="noopener" target="_blank" title="github.com">
        <svg viewBox="0 0 480 512" xmlns="http://www.w3.org/2000/svg"><path d="M186.1 328.7c0 20.9-10.9 55.1-36.7 55.1s-36.7-34.2-36.7-55.1 10.9-55.1 36.7-55.1 36.7 34.2 36.7 55.1zM480 278.2c0 31.9-3.2 65.7-17.5 95-37.9 76.6-142.1 74.8-216.7 74.8-75.8 0-186.2 2.7-225.6-74.8-14.6-29-20.2-63.1-20.2-95 0-41.9 13.9-81.5 41.5-113.6-5.2-15.8-7.7-32.4-7.7-48.8 0-21.5 4.9-32.3 14.6-51.8 45.3 0 74.3 9 108.8 36 29-6.9 58.8-10 88.7-10 27 0 54.2 2.9 80.4 9.2 34-26.7 63-35.2 107.8-35.2 9.8 19.5 14.6 30.3 14.6 51.8 0 16.4-2.6 32.7-7.7 48.2 27.5 32.4 39 72.3 39 114.2zm-64.3 50.5c0-43.9-26.7-82.6-73.5-82.6-18.9 0-37 3.4-56 6-14.9 2.3-29.8 3.2-45.1 3.2-15.2 0-30.1-.9-45.1-3.2-18.7-2.6-37-6-56-6-46.8 0-73.5 38.7-73.5 82.6 0 87.8 80.4 101.3 150.4 101.3h48.2c70.3 0 150.6-13.4 150.6-101.3zm-82.6-55.1c-25.8 0-36.7 34.2-36.7 55.1s10.9 55.1 36.7 55.1 36.7-34.2 36.7-55.1-10.9-55.1-36.7-55.1z"></path></svg>
    </a>
    <a class="md-footer-social__link" href="https://twitter.com/up42_" rel="noopener" target="_blank" title="twitter.com">
        <svg viewBox="0 0 512 512" xmlns="http://www.w3.org/2000/svg"><path d="M459.37 151.716c.325 4.548.325 9.097.325 13.645 0 138.72-105.583 298.558-298.558 298.558-59.452 0-114.68-17.219-161.137-47.106 8.447.974 16.568 1.299 25.34 1.299 49.055 0 94.213-16.568 130.274-44.832-46.132-.975-84.792-31.188-98.112-72.772 6.498.974 12.995 1.624 19.818 1.624 9.421 0 18.843-1.3 27.614-3.573-48.081-9.747-84.143-51.98-84.143-102.985v-1.299c13.969 7.797 30.214 12.67 47.431 13.319-28.264-18.843-46.781-51.005-46.781-87.391 0-19.492 5.197-37.36 14.294-52.954 51.655 63.675 129.3 105.258 216.365 109.807-1.624-7.797-2.599-15.918-2.599-24.04 0-57.828 46.782-104.934 104.934-104.934 30.213 0 57.502 12.67 76.67 33.137 23.715-4.548 46.456-13.32 66.599-25.34-7.798 24.366-24.366 44.833-46.132 57.827 21.117-2.273 41.584-8.122 60.426-16.243-14.292 20.791-32.161 39.308-52.628 54.253z"></path></svg>
    </a>
    <a class="md-footer-social__link" href="https://www.linkedin.com/company/up42/" rel="noopener" target="_blank" title="www.linkedin.com">
        <svg viewBox="0 0 448 512" xmlns="http://www.w3.org/2000/svg"><path d="M416 32H31.9C14.3 32 0 46.5 0 64.3v383.4C0 465.5 14.3 480 31.9 480H416c17.6 0 32-14.5 32-32.3V64.3c0-17.8-14.4-32.3-32-32.3zM135.4 416H69V202.2h66.5V416zm-33.2-243c-21.3 0-38.5-17.3-38.5-38.5S80.9 96 102.2 96c21.2 0 38.5 17.3 38.5 38.5 0 21.3-17.2 38.5-38.5 38.5zm282.1 243h-66.4V312c0-24.8-.5-56.7-34.5-56.7-34.6 0-39.9 27-39.9 54.9V416h-66.4V202.2h63.7v29.2h.9c8.9-16.8 30.6-34.5 62.9-34.5 67.2 0 79.7 44.3 79.7 101.9V416z"></path></svg>
    </a>
    <a class="md-footer-social__link" href="mailto:support@up42.com" rel="noopener" target="_blank" title="">
        <svg viewBox="0 0 512 512" xmlns="http://www.w3.org/2000/svg"><path d="M502.3 190.8c3.9-3.1 9.7-.2 9.7 4.7V400c0 26.5-21.5 48-48 48H48c-26.5 0-48-21.5-48-48V195.6c0-5 5.7-7.8 9.7-4.7 22.4 17.4 52.1 39.5 154.1 113.6 21.1 15.4 56.7 47.8 92.2 47.6 35.7.3 72-32.8 92.3-47.6 102-74.1 131.6-96.3 154-113.7zM256 320c23.2.4 56.6-29.2 73.4-41.4 132.7-96.3 142.8-104.7 173.4-128.7 5.8-4.5 9.2-11.5 9.2-18.9v-19c0-26.5-21.5-48-48-48H48C21.5 64 0 85.5 0 112v19c0 7.4 3.4 14.3 9.2 18.9 30.6 23.9 40.7 32.4 173.4 128.7 16.8 12.2 50.2 41.8 73.4 41.4z"></path></svg>
    </a>
    </div>
</div>
