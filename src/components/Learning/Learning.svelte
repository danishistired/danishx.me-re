<script lang="ts">
  import { slide } from "svelte/transition";

  interface Learning {
    title: string;
    description: string;
    date: string;
  }

  const learnings: Learning[] = [
    {
      title: "Astro",
      description:
        "been really liking astro, reminds me of svelte, but even better for content driven static sites.",
      date: "2025-01",
    },
    {
      title: "huggingface api",
      description:
        "started using free apis for some demanding problems in hackathons.",
      date: "2024-11",
    },
    {
      title: "unity and vr",
      description:
        "been working on a vr game in unity as part of a university project. uff, not a big fan of unity.",
      date: "2024-10",
    },
    {
      title: "flutter",
      description: "switched from figma to flutter and never looked back. i use it to make all my applications including my most successful project ecomitra.",
      date: "2024-09",
    },
    {
      title: "figma",
      description:
        "playing around a bit designing some websites and app wireframes in figma",
      date: "2024-08",
    },
    {
      title: "svelte and sveltekit",
      description:
        "love svelte, my favourite framework for web development. i use it for most of my personal projects, including this website.",
      date: "2024-06",
    },
    {
      title: "tailwind",
      description: "the best bad idea in web development. better than pure css by far. used in most of my newer projects including this website.",
      date: "2023-05",
    },
    {
      title: "blender",
      description:
        'making some low poly donuts in blender, lots of fun once you get over the "i\'m overwhelmed" feeling',
      date: "2023-01",
    },
    {
      title: "html",
      description:
        "wanted to design websites, so html was the next language to go to.",
      date: "2022-06",
    },
    {
      title: "python",
      description:
        "just to figure out this whole coding thing, i started with the language google told me was the easiest to learn",
      date: "2022-03",
    },
  ];

  function formatDate(date: string) {
    return new Date(date)
      .toLocaleDateString("en-US", {
        year: "numeric",
        month: "long",
      })
      .toLowerCase();
  }

  let showAll = false;

  $: shownLearnings = showAll ? learnings : [...learnings].slice(0, 3);
</script>

<div class="relative isolate overflow-hidden bg-background">
  <div class="mx-auto max-w-5xl px-6 lg:px-8">
    <div id="learning" class="py-16 md:py-32 section">
      <div class="max-w-2xl">
        <h1
          class="text-4xl font-bold tracking-tight text-base-800 dark:text-base-100 sm:text-5xl"
        >
          always keep learning
        </h1>
        <p class="mt-6 text-base text-base-600 dark:text-base-400">
          one of the things i love most about programming is that there's always
          something new to learn. here's a selection of some of the things i've
          been learning lately:
        </p>
      </div>
      <div
        class="mt-16 md:border-l md:border-base-100 md:pl-6 md:dark:border-base-700/40"
      >
        <div class="flex max-w-3xl flex-col space-y-16">
          {#each shownLearnings as learning}
            <article
              transition:slide
              class="md:grid md:grid-cols-4 md:items-baseline"
            >
              <div
                class="group relative flex flex-col items-start md:col-span-3"
              >
                <div
                  class="text-base font-semibold tracking-tight text-base-800 dark:text-base-100"
                >
                  {learning.title}
                </div>
                <div
                  class="relative z-10 order-first mb-3 flex items-center text-sm text-base-400 dark:text-base-500 pl-3.5 mt-1 md:hidden"
                >
                  <span
                    class="absolute inset-y-0 left-0 flex items-center"
                    aria-hidden="true"
                  >
                    <span
                      class="h-4 w-0.5 rounded-full bg-base-200 dark:bg-base-500"
                    />
                  </span>
                  {formatDate(learning.date)}
                </div>

                <p
                  class="relative z-10 mt-2 text-sm text-base-600 dark:text-base-400"
                >
                  {learning.description}
                </p>
              </div>
              <div
                class="relative z-10 order-first mb-3 items-center text-sm text-base-400 dark:text-base-500 mt-1 hidden md:block"
              >
                {formatDate(learning.date)}
              </div>
            </article>
          {/each}

          {#if !showAll}
            <div class="justify-center flex">
              <button
                on:click={() => (showAll = true)}
                type="button"
                class="group flex items-center rounded-full mr-4 bg-white/90 px-4 py-2 text-sm font-medium text-base-800 shadow-lg shadow-base-800/5 ring-1 ring-base-900/5 backdrop-blur dark:bg-white/5 dark:text-base-200 dark:ring-white/10 dark:hover:ring-white/20"
                aria-label="Update dimensions"
              >
                show more

                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  fill="none"
                  viewBox="0 0 24 24"
                  stroke-width="1.5"
                  stroke="currentColor"
                  class="ml-2 h-auto w-4 stroke-base-500 group-hover:stroke-base-700 dark:group-hover:stroke-base-400"
                >
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    d="m19.5 8.25-7.5 7.5-7.5-7.5"
                  />
                </svg>
              </button>
            </div>
          {/if}
        </div>
      </div>
    </div>
  </div>
</div>
