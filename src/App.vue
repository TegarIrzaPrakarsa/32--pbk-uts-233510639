<template>
  <div class="app">
    <h1>📝 Daftar Kegiatan</h1>

    <div class="input-section">
      <input v-model="newTask" @keyup.enter="addTask" placeholder="Tambahkan kegiatan..." />
      <button @click="addTask">Tambah</button>
    </div>

    <div class="filter">
      <label>
        <input type="checkbox" v-model="showOnlyIncomplete" />
        Tampilkan hanya yang belum selesai
      </label>
    </div>

    <ul class="task-list">
      <li
        v-for="(task, index) in filteredTasks"
        :key="index"
        :class="{ done: task.completed }"
      >
        <input type="checkbox" v-model="task.completed" />
        <span>{{ task.text }}</span>
        <button @click="removeTask(index)">❌</button>
      </li>
    </ul>
  </div>
</template>