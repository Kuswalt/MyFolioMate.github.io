<script lang="ts">
    export let portfolio;
    export let projects;
  </script>
  
  <div class="container mx-auto px-4 py-8">
    <div class="max-w-4xl mx-auto">
      <header class="mb-12 text-center">
        <h1 class="text-5xl font-bold mb-4" style="color: {portfolio.theme_color}">
          {portfolio.title || 'My Portfolio'}
        </h1>
        <p class="text-xl text-gray-600 mb-6">{portfolio.about}</p>
        {#if portfolio.social_links}
          <div class="flex justify-center space-x-4">
            {#each portfolio.social_links.split(',') as link}
              <a 
                href={link.trim()} 
                target="_blank" 
                class="text-blue-600 hover:text-blue-800"
                style="color: {portfolio.theme_color}"
              >
                {link.includes('linkedin') ? 'LinkedIn' : 
                 link.includes('github') ? 'GitHub' : 
                 link.includes('twitter') ? 'Twitter' : 'Link'}
              </a>
            {/each}
          </div>
        {/if}
      </header>
  
      <div class="grid grid-cols-1 md:grid-cols-2 gap-8 mb-12">
        <section class="bg-gray-50 p-8 rounded-lg">
          <h2 class="text-2xl font-bold mb-6" style="color: {portfolio.theme_color}">Education</h2>
          <div class="prose">
            {@html portfolio.education || 'No education listed yet.'}
          </div>
        </section>
  
        <section class="bg-gray-50 p-8 rounded-lg">
          <h2 class="text-2xl font-bold mb-6" style="color: {portfolio.theme_color}">Achievements</h2>
          <div class="prose">
            {@html portfolio.achievements || 'No achievements listed yet.'}
          </div>
        </section>
      </div>
  
      <section class="mb-12">
        <h2 class="text-2xl font-bold mb-6" style="color: {portfolio.theme_color}">Skills</h2>
        <div class="flex flex-wrap gap-3">
          {#each portfolio.skills as skill}
            <span 
              class="px-4 py-2 rounded-full text-white"
              style="background-color: {portfolio.theme_color}"
            >
              {skill}
            </span>
          {/each}
        </div>
      </section>
  
      <section class="mb-12">
        <h2 class="text-2xl font-bold mb-6" style="color: {portfolio.theme_color}">Featured Projects</h2>
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
          {#each projects as project}
            <div class="border rounded-lg p-6 hover:shadow-lg transition-all duration-300">
              <h3 class="text-xl font-bold mb-3">{project.title}</h3>
              <p class="text-gray-600 mb-4">{project.description}</p>
              <a 
                href={project.project_url} 
                target="_blank" 
                class="inline-flex items-center hover:opacity-80 transition-opacity"
                style="color: {portfolio.theme_color}"
              >
                View Project
                <svg class="ml-2 w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14 5l7 7m0 0l-7 7m7-7H3" />
                </svg>
              </a>
            </div>
          {/each}
        </div>
      </section>
  
      <section class="bg-gray-50 p-8 rounded-lg">
        <h2 class="text-2xl font-bold mb-6" style="color: {portfolio.theme_color}">Contact</h2>
        <div class="prose max-w-none">
          {@html portfolio.contact_info}
        </div>
      </section>
    </div>
  </div>