<template functional>
  <div class="home-layout display flex-coulmn">
    <header class="home-layout-header">
      <slot name="home-header"></slot>
    </header>
    <div class="home-layout-content">
      <slot name="home-content"></slot>
    </div>
    <div class="home-layout-bottom">
      <slot name="home-bottom"></slot>
    </div>
  </div>
</template>
