<script>

</script>
<template>
<div class="flex items-center justify-center w-full h-screen font-algerian">
  <div class="px-4 lg:py-12">
    <div class="lg:gap-4 lg:flex">
      <div
        class="flex flex-col items-center justify-center md:py-24 lg:py-32"
      >
        <h1 class="font-bold text-red-800 text-9xl">404</h1>
        <p
          class="mb-2 text-2xl font-bold text-center text-gray-800 md:text-3xl"
        >
          <span class="text-red-500">Oops!</span> Page non trouvée
        </p>
        <p class="mb-8 text-center text-gray-500 md:text-lg">
          La page que vous recherchez n'existe pas...
        </p>
        <RouterLink to="/" class="px-6 py-2 text-sm font-semibold text-blue-700 bg-blue-100"
          >Accueil</RouterLink>
              <p class="mb-8 text-center text-gray-500 md:text-lg">
          Vous cherchiez peut-être ?
        </p>
                <a href="https://fabiogafforelli.fr" class="px-6 py-2 text-sm font-semibold text-red-700 bg-red-100"
          >Le FAB ?</a>
          <br>
         
                </div>
    </div>
  </div>
</div>
</template>