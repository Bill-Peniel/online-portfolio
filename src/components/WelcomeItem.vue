<template>
  <div class="mt-8 flex relative bg-white dark:bg-gray-900 rounded-lg shadow p-6 border border-gray-200 dark:border-gray-700 transition-colors">
    <i class="flex items-center justify-center w-12 h-12 md:w-[50px] md:h-[50px] absolute md:static left-0 top-1/2 md:top-0 md:left-0 -translate-y-1/2 md:translate-y-0 border border-gray-300 dark:border-gray-600 bg-gray-50 dark:bg-gray-800 rounded-lg text-primary-600 dark:text-primary-400 shadow">
      <slot name="icon"></slot>
    </i>
    <div class="flex-1 ml-4">
      <h3 class="text-lg font-semibold mb-2 text-gray-900 dark:text-gray-100">
        <slot name="heading"></slot>
      </h3>
      <div class="text-gray-700 dark:text-gray-300">
        <slot></slot>
      </div>
    </div>
  </div>
</template>
