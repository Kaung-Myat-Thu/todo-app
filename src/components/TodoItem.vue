<template>
  <div>
    <ul>
      <li
        v-for="task in tasks"
        :key="task.id"
        class="bg-slate-200 rounded-sm flex justify-between items-center shadow-sm w-96 text-xl text-orange-500 my-4 px-4 py-2 mx-auto"
      >
        <div>{{ task.task }}</div>
        <button
          @click="$emit('delete-task', task.id)"
          class="text-red-500 font-bold cursor-pointer"
        >
          x
        </button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    tasks: Array,
  },
};
</script>
