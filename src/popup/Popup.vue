<script setup lang="ts">
async function handelGetJDCookie() {
  // 获取'pt_pin'和'pt_key'的cookie
  const pt_key = await browser.cookies.getAll({
    domain: '.jd.com',
    name: 'pt_key',
  })
  const pt_pin = await browser.cookies.getAll({
    domain: '.jd.com',
    name: 'pt_pin',
  })
  // 将cookie信息复制到剪切板
  const cookie = `${pt_key[0].name}=${pt_key[0].value};${pt_pin[0].name}=${pt_pin[0].value};`
  await navigator.clipboard.writeText(cookie)
}
</script>

<template>
  <main class="w-[200px] px-4 py-5 text-center text-gray-700">
    <Logo />
    <p />

    <button class="btn mt-2" @click="handelGetJDCookie">
      获取京东Cookie
    </button>
  </main>
</template>
