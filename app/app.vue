<template>
  <UContainer class="py-10">
    <h1 class="text-3xl font-bold mb-6">Plataforma de Trocas!</h1>

    <div v-if="pending"></div>

    <div v-else class="bg-gray-100 p-4 rounded-lg dark:bg-gray-800">
      <pre>{{ products }}</pre>
    </div>
  </UContainer>
</template>

<script setup>
// 1. Chamar a ferramenta do Supabase
const supabase = useSupabaseClient()

// 2. Ir à tabela 'produtos' e buscar tudo (*)
const { data: products, pending } = await useAsyncData('products', async () => {
  const { data } = await supabase.from('products').select('*')
  return data
})
</script>
