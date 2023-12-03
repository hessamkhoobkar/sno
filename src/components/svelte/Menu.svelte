<script>
  import { fly } from "svelte/transition";
  import { cubicInOut } from "svelte/easing";

  function clickOutside(element, callbackFunction) {
    function onClick(event) {
      if (!element.contains(event.target)) {
        callbackFunction();
      }
    }

    document.body.addEventListener("click", onClick);

    return {
      update(newCallbackFunction) {
        callbackFunction = newCallbackFunction;
      },
      destroy() {
        document.body.removeEventListener("click", onClick);
      },
    };
  }

  let isMenuOpen = false;
  const handleMenuClick = () => {
    isMenuOpen = !isMenuOpen;
  };

  const linksData = [
    {
      title: "Home Pages",
      links: [
        {
          name: "Two columns",
          url: "/homepages/two-column",
        },
        {
          name: "Three columns",
          url: "/homepages/three-column",
        },
        {
          name: "One columns with sidebar",
          url: "/homepages/one-column-sidebar",
        },
        {
          name: "Two columns with sidebar",
          url: "/homepages/two-column-sidebar",
        },
      ],
    },
    {
      title: "Pages",
      links: [
        {
          name: "Home",
          url: "/",
        },
        {
          name: "About",
          url: "/about",
        },
        {
          name: "Contact",
          url: "/contact",
        },
      ],
    },
  ];
</script>

<div
  use:clickOutside={() => {
    isMenuOpen = false;
  }}
>
  <button
    onclick={handleMenuClick}
    class="header-button flex justify-start items-center gap-4 text-3xl py-10 pe-8"
  >
    <svg
      xmlns="http://www.w3.org/2000/svg"
      width="1em"
      height="1em"
      viewBox="-5 -7 24 24"
    >
      <path
        fill="currentColor"
        d="M1 0h5a1 1 0 1 1 0 2H1a1 1 0 1 1 0-2m7 8h5a1 1 0 0 1 0 2H8a1 1 0 1 1 0-2M1 4h12a1 1 0 0 1 0 2H1a1 1 0 1 1 0-2"
      ></path>
    </svg>

    <span class="text-xs uppercase tracking-[0.3em]">menu</span>
  </button>

  {#if isMenuOpen}
    <div
      class="absolute inset-0 top-28 h-min z-20 bg-white menu-shadow p-4"
      transition:fly={{
        delay: 0,
        duration: 750,
        x: 0,
        y: -64,
        opacity: 0,
        easing: cubicInOut,
      }}
    >
      <div class="w-full max-w-7xl mx-auto flex justify-start items-stretch">
        {#each linksData as group, index}
          <div
            class={`flex flex-col justify-start items-start border-stone-200 grow ${
              index === 0 ? "" : "border-l pl-4"
            }`}
          >
            <span class="font-sans text-sm text-stone-600 mb-4">
              {group.title}
            </span>
            {#each group.links as link}
              <a
                class="relative font-serif text-lg font-bold block"
                href={link.url}
              >
                <span>
                  {link.name}
                </span>
                <span
                  class="absolute block inset-0 underline opacity-0 hover:opacity-100 duration-300 ease-in-out"
                >
                  {link.name}
                </span>
              </a>
            {/each}
          </div>
        {/each}
      </div>
    </div>
  {/if}
</div>

<style>
  .menu-shadow {
    box-shadow: -1px 61px 73px -37px rgba(0, 0, 0, 0.79);
    -webkit-box-shadow: -1px 61px 73px -37px rgba(0, 0, 0, 0.79);
    -moz-box-shadow: -1px 61px 73px -37px rgba(0, 0, 0, 0.79);
  }
</style>
