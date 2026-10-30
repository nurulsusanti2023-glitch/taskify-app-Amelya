
<script setup>
import { ref } from 'vue'

// Menyimpan daftar tugas
const tasks = ref([])

// Menyimpan input tugas
const inputTask = ref('')

// Menambahkan tugas baru
const addTask = (title) => {
  if (!title || !title.trim()) return

  const newTask = {
    id: new Date().getTime(),
    title: title.trim(),
    status: false
  }

  tasks.value.push(newTask)
  inputTask.value = ''
}

// Menghapus tugas
const deleteTask = (id) => {
  const task = tasks.value.find(item => item.id === id)

  if (!task) {
    alert('Task tidak ditemukan')
    return
  }

  const confirmation = confirm(
    'Apakah anda yakin ingin menghapus?'
  )

  if (confirmation) {
    tasks.value = tasks.value.filter(
      item => item.id !== id
    )
  }
}
</script>

<template>
  <main class="taskify-page">
    <div class="taskify-container">

      <!-- Header -->
      <header class="hero">
        <div class="brand">
          <div class="brand-icon">
            <svg viewBox="0 0 64 64" fill="none">
              <rect x="13" y="11" width="38" height="45"
                rx="9" stroke="currentColor" stroke-width="4"/>
              <rect x="24" y="6" width="16" height="10"
                rx="4" fill="currentColor"/>
              <path d="M22 34L29 41L43 26"
                stroke="currentColor" stroke-width="5"
                stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
          </div>

          <div class="brand-text">
            <h1>Taskify <span>Vue</span></h1>
            <p>Atur tugas, raih produktivitas, capai tujuanmu.</p>
          </div>
        </div>

        <form class="task-form" @submit.prevent="addTask(inputTask)">
          <div class="input-wrap">
            <svg viewBox="0 0 24 24" fill="none">
              <circle cx="10.8" cy="10.8" r="6.8"
                stroke="currentColor" stroke-width="2.2"/>
              <path d="M16 16L21 21"
                stroke="currentColor" stroke-width="2.2"
                stroke-linecap="round"/>
            </svg>

            <input
              v-model="inputTask"
              type="text"
              placeholder="Masukkan tugas baru"
              aria-label="Tugas baru"
            />
          </div>

          <button type="submit" class="add-button">
            <span class="plus">+</span>
            Tambah
          </button>
        </form>
      </header>

      <!-- Daftar tugas -->
      <section class="task-layout">
        <!-- Kartu besar -->
        <article class="task-card card-purple featured-card">
          <div class="card-top">
            <div class="category-icon purple-icon">
              ✦
            </div>
            <span class="category-label">Produktivitas</span>
          </div>

          <h2>Daftar Tugas</h2>
          <p class="card-description">
            Selesaikan tugas dengan konsisten, langkah kecil
            yang berarti.
          </p>

          <div class="big-illustration clipboard-art">
            <svg viewBox="0 0 300 250" fill="none">
              <ellipse cx="150" cy="206" rx="105" ry="19"
                fill="#B9B5FF" opacity=".35"/>
              <rect x="72" y="36" width="144" height="181"
                rx="24" fill="#7375F5" opacity=".22"
                transform="rotate(-7 72 36)"/>
              <rect x="83" y="39" width="133" height="174"
                rx="20" fill="#6575F5"
                transform="rotate(-7 83 39)"/>
              <rect x="93" y="49" width="113" height="151"
                rx="13" fill="#F8FAFF"
                transform="rotate(-7 93 49)"/>
              <rect x="126" y="30" width="52" height="25"
                rx="9" fill="#445CE8"
                transform="rotate(-7 126 30)"/>
              <circle cx="152" cy="39" r="7"
                fill="#E7ECFF" stroke="#354AC5" stroke-width="4"/>
              <rect x="111" y="83" width="22" height="22"
                rx="5" fill="#7375F5"/>
              <path d="M116 94L122 100L130 88"
                stroke="white" stroke-width="3"
                stroke-linecap="round" stroke-linejoin="round"/>
              <path d="M145 92H183M145 101H173"
                stroke="#B7BDFD" stroke-width="6"
                stroke-linecap="round"/>
              <rect x="113" y="119" width="19" height="19"
                rx="5" stroke="#9298FF" stroke-width="4"/>
              <path d="M145 126H183M145 135H173"
                stroke="#B7BDFD" stroke-width="6"
                stroke-linecap="round"/>
              <rect x="116" y="155" width="19" height="19"
                rx="5" stroke="#9298FF" stroke-width="4"/>
              <path d="M148 162H181"
                stroke="#B7BDFD" stroke-width="6"
                stroke-linecap="round"/>
              <g transform="rotate(24 224 157)">
                <rect x="207" y="105" width="23" height="105"
                  rx="7" fill="#FFB629"/>
                <rect x="207" y="105" width="23" height="17"
                  rx="5" fill="#FF79AD"/>
                <path d="M207 210L218.5 230L230 210Z"
                  fill="#E7B18C"/>
                <path d="M215 224L218.5 230L222 224Z"
                  fill="#34466E"/>
              </g>
              <path d="M237 60L251 43M249 77L266 68M62 125L46 115"
                stroke="#7967F5" stroke-width="8"
                stroke-linecap="round"/>
            </svg>
          </div>

          <div class="featured-footer">
            <span class="mini-dot"></span>
            Satu langkah setiap hari
          </div>
        </article>

        <!-- Tugas pertama -->
        <article class="task-card card-pink">
          <div class="card-top">
            <div class="category-icon pink-icon">♥</div>
            <span class="category-label">Personal</span>
          </div>

          <h2>nama</h2>
          <p class="card-description">
            Jaga nama, jaga kepercayaan.
          </p>

          <div class="small-illustration identity-art">
            <svg viewBox="0 0 150 120" fill="none">
              <ellipse cx="76" cy="100" rx="55" ry="12"
                fill="#F5A7CF" opacity=".3"/>
              <rect x="30" y="20" width="90" height="75"
                rx="17" fill="#FFB5D7"/>
              <rect x="37" y="27" width="76" height="60"
                rx="12" fill="#FFF9FD"/>
              <rect x="61" y="9" width="27" height="26"
                rx="10" fill="#5E91FF"/>
              <circle cx="74.5" cy="21" r="6"
                fill="#CBE3FF"/>
              <circle cx="61" cy="49" r="10"
                fill="#5A9AFF"/>
              <path d="M44 74C45 62 53 58 61 58C69 58 77 63 78 74"
                fill="#5A9AFF"/>
              <rect x="83" y="45" width="20" height="6"
                rx="3" fill="#A6C3FF"/>
              <rect x="83" y="57" width="20" height="6"
                rx="3" fill="#A6C3FF"/>
              <rect x="83" y="69" width="14" height="6"
                rx="3" fill="#A6C3FF"/>
            </svg>
          </div>
        </article>

        <!-- Tugas kedua -->
        <article class="task-card card-yellow">
          <div class="card-top">
            <div class="category-icon yellow-icon">★</div>
            <span class="category-label">Inspirasi</span>
          </div>

          <h2>amel</h2>
          <p class="card-description">
            Jadilah versi terbaik dari diri sendiri.
          </p>

          <div class="small-illustration star-art">
            <svg viewBox="0 0 150 120" fill="none">
              <ellipse cx="76" cy="102" rx="51" ry="11"
                fill="#FFD86A" opacity=".3"/>
              <path d="M75 12L91 43L125 48L100 72L106 106L75 90L44 106L50 72L25 48L59 43Z"
                fill="#FFC52E" stroke="#FFAE00" stroke-width="3"
                stroke-linejoin="round"/>
              <circle cx="64" cy="63" r="3.5" fill="#534C65"/>
              <circle cx="86" cy="63" r="3.5" fill="#534C65"/>
              <path d="M67 75Q75 84 83 75"
                stroke="#B66B24" stroke-width="3"
                stroke-linecap="round"/>
              <path d="M18 37L10 29M120 27L127 18M130 76L139 72"
                stroke="#FFB800" stroke-width="5"
                stroke-linecap="round"/>
            </svg>
          </div>
        </article>

        <!-- Tugas ketiga -->
        <article class="task-card card-mint">
          <div class="card-top">
            <div class="category-icon mint-icon">✓</div>
            <span class="category-label">Pekerjaan</span>
          </div>

          <h2>kerja</h2>
          <p class="card-description">
            Kerja hari ini, hasil untuk nanti.
          </p>

          <div class="small-illustration laptop-art">
            <svg viewBox="0 0 220 130" fill="none">
              <ellipse cx="111" cy="112" rx="85" ry="9"
                fill="#79DCC8" opacity=".3"/>
              <rect x="39" y="16" width="123" height="79"
                rx="9" fill="#355FD8"
                transform="rotate(3 39 16)"/>
              <rect x="47" y="24" width="107" height="61"
                rx="5" fill="#729CFF"
                transform="rotate(3 47 24)"/>
              <path d="M86 51L99 64L121 42"
                stroke="white" stroke-width="8"
                stroke-linecap="round" stroke-linejoin="round"/>
              <path d="M29 97L172 104L195 114Q198 119 190 120H28Q19 118 29 97Z"
                fill="#4779F1" stroke="#315FD4" stroke-width="2"/>
              <path d="M83 108H133"
                stroke="#A7C1FF" stroke-width="4"
                stroke-linecap="round"/>
              <path d="M178 80L178 48M178 64Q160 57 158 43M179 73Q196 67 201 52"
                stroke="#23B89B" stroke-width="5"
                stroke-linecap="round"/>
              <path d="M164 90Q177 78 190 90L188 105H166Z"
                fill="#F5FFFD" stroke="#9DDED2" stroke-width="2"/>
            </svg>
          </div>
        </article>

      </section>

      <!-- Daftar tugas asli dari Vue -->
      <section class="live-section">
        <div class="section-heading">
          <div>
            <span class="eyebrow">RUANG KERJA</span>
            <h2>Tugas Saya</h2>
          </div>

          <span class="task-count">
            {{ tasks.length }} tugas
          </span>
        </div>

        <div v-if="tasks.length === 0" class="empty-state">
          <div class="empty-icon">✦</div>
          <h3>Belum ada tugas baru</h3>
          <p>Tambahkan tugas melalui kolom di atas.</p>
        </div>

        <ul v-else class="live-list">
          <li
            v-for="task in tasks"
            :key="task.id"
            class="live-item"
            :class="{ completed: task.status }"
          >
            <label class="task-label">
              <input
                v-model="task.status"
                type="checkbox"
                class="task-checkbox"
              />

              <span class="live-task-title">
                {{ task.title }}
              </span>
            </label>

            <button
              @click="deleteTask(task.id)"
              class="delete-button"
              type="button"
              aria-label="Hapus tugas"
            >
              <svg viewBox="0 0 24 24" fill="none">
                <path d="M4 7H20M9 7V4H15V7M7 7L8 20H16L17 7M10 11V16M14 11V16"
                  stroke="currentColor" stroke-width="2"
                  stroke-linecap="round" stroke-linejoin="round"/>
              </svg>
              Hapus
            </button>
          </li>
        </ul>
      </section>

      <footer class="page-footer">
        <span>✦</span>
        Buat harimu lebih produktif bersama Taskify Vue
      </footer>
    </div>
  </main>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Nunito:wght@400;500;600;700;800;900&display=swap');

:root {
  font-family: 'Nunito', sans-serif;
  color: #19294d;
  background: #f8faff;
  font-synthesis: none;
  text-rendering: optimizeLegibility;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

* {
  box-sizing: border-box;
}

body {
  margin: 0;
  min-width: 320px;
  min-height: 100vh;
}

button,
input {
  font: inherit;
}

button {
  -webkit-tap-highlight-color: transparent;
}

.taskify-page {
  min-height: 100vh;
  padding: 28px 32px;
  overflow: hidden;
  background:
    radial-gradient(ellipse at 8% 2%, #176f91 0, transparent 26%),
    radial-gradient(ellipse at 92% 92%, #4d73d1 0, transparent 28%),
    linear-gradient(135deg, #0b1934, #4763d5 55%, #fffaff);
}

.taskify-container {
  max-width: 1500px;
  margin: 0 auto;
}

/* Header */

.hero {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 28px;
  padding: 23px 28px;
  border: 1px solid rgba(255,255,255,.9);
  border-radius: 30px;
  background: linear-gradient(115deg, #e6edff, #eef5ff);
  box-shadow:
    10px 14px 30px rgba(101,125,190,.12),
    inset 2px 2px 5px rgba(255,255,255,.95);
}

.brand {
  display: flex;
  align-items: center;
  gap: 25px;
  min-width: 0;
}

.brand-icon {
  display: grid;
  flex-shrink: 0;
  place-items: center;
  width: 100px;
  height: 100px;
  padding: 18px;
  color: #4776ff;
  border: 1px solid rgba(255,255,255,.9);
  border-radius: 26px;
  background: linear-gradient(145deg, #f5f8ff, #e0e9ff);
  box-shadow:
    8px 10px 20px rgba(89,121,226,.18),
    inset 3px 3px 7px white;
}

.brand-icon svg {
  width: 100%;
  height: 100%;
}

.brand-text h1 {
  margin: 0;
  color: #182744;
  font-size: clamp(32px, 3.3vw, 56px);
  font-weight: 900;
  letter-spacing: -1.8px;
  line-height: 1.1;
}

.brand-text h1 span {
  color: #5969ff;
}

.brand-text p {
  margin: 10px 0 0;
  color: #7184af;
  font-size: clamp(13px, 1.3vw, 19px);
  font-weight: 600;
}

.task-form {
  display: flex;
  align-items: center;
  gap: 16px;
  width: min(54%, 690px);
}

.input-wrap {
  display: flex;
  align-items: center;
  gap: 13px;
  flex: 1;
  min-width: 0;
  height: 62px;
  padding: 0 20px;
  border: 1px solid #dce5ff;
  border-radius: 21px;
  background: rgba(255,255,255,.94);
  box-shadow:
    5px 7px 16px rgba(104,129,197,.11),
    inset 2px 2px 4px rgba(220,229,250,.35);
  transition: border-color .2s, box-shadow .2s;
}

.input-wrap:focus-within {
  border-color: #9baaff;
  box-shadow: 0 0 0 4px rgba(102,120,255,.12);
}

.input-wrap svg {
  width: 26px;
  height: 26px;
  flex-shrink: 0;
  color: #8093bb;
}

.input-wrap input {
  width: 100%;
  min-width: 0;
  border: 0;
  outline: 0;
  color: #253658;
  background: transparent;
  font-size: 16px;
  font-weight: 600;
}

.input-wrap input::placeholder {
  color: #8798bd;
}

.add-button {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 11px;
  min-height: 62px;
  padding: 0 24px;
  flex-shrink: 0;
  border: 1px solid rgba(255,255,255,.55);
  border-radius: 20px;
  color: white;
  background: linear-gradient(135deg, #7984ff, #4e5fff);
  box-shadow:
    0 9px 18px rgba(81,99,255,.24),
    inset 2px 2px 4px rgba(255,255,255,.4),
    inset -3px -4px 6px rgba(43,55,197,.13);
  font-size: 17px;
  font-weight: 800;
  cursor: pointer;
  transition: transform .2s, box-shadow .2s;
}

.add-button:hover {
  transform: translateY(-2px);
  box-shadow: 0 13px 23px rgba(81,99,255,.3);
}

.plus {
  font-size: 28px;
  font-weight: 500;
  line-height: 1;
}

/* Kartu pastel */

.task-layout {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  grid-template-rows: repeat(2, minmax(230px, auto));
  gap: 20px;
  margin-top: 24px;
}

.task-card {
  position: relative;
  min-width: 0;
  min-height: 230px;
  padding: 26px;
  overflow: hidden;
  border: 1px solid rgba(255,255,255,.9);
  border-radius: 29px;
  box-shadow:
    12px 14px 27px rgba(108,128,181,.12),
    -5px -5px 15px rgba(255,255,255,.75),
    inset 2px 2px 5px rgba(255,255,255,.65);
  transition: transform .25s, box-shadow .25s;
}

.task-card:hover {
  transform: translateY(-4px);
  box-shadow:
    16px 20px 32px rgba(108,128,181,.16),
    -5px -5px 15px white;
}

.card-purple {
  background: linear-gradient(145deg, #f0edff, #e4e1ff);
}

.card-pink {
  background: linear-gradient(145deg, #fff0f6, #ffe3f0);
}

.card-yellow {
  background: linear-gradient(145deg, #fff8e1, #fff0c9);
}

.card-mint {
  background: linear-gradient(145deg, #e9faf6, #d6f4ed);
}

.featured-card {
  grid-row: span 2;
  min-height: 480px;
}

.card-top {
  position: relative;
  z-index: 1;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 10px;
  margin-bottom: 15px;
}

.category-icon {
  display: grid;
  place-items: center;
  width: 54px;
  height: 54px;
  border-radius: 50%;
  font-size: 27px;
  font-weight: 900;
  box-shadow:
    4px 5px 10px rgba(115,119,180,.08),
    inset 2px 2px 5px rgba(255,255,255,.8);
}

.purple-icon {
  color: #7962f7;
  background: #e4dcff;
}

.pink-icon {
  color: #f75d9e;
  background: #ffd5e7;
}

.yellow-icon {
  color: #f5ae00;
  background: #fff0b9;
}

.mint-icon {
  color: #14af91;
  background: #c8f1e6;
}

.category-label {
  padding: 7px 12px;
  border: 1px solid rgba(255,255,255,.85);
  border-radius: 999px;
  color: #7885a8;
  background: rgba(255,255,255,.45);
  font-size: 11px;
  font-weight: 800;
  letter-spacing: .6px;
  text-transform: uppercase;
}

.task-card h2 {
  position: relative;
  z-index: 1;
  margin: 0 0 8px;
  color: #19294d;
  font-size: 29px;
  font-weight: 900;
  letter-spacing: -.5px;
}

.card-description {
  position: relative;
  z-index: 1;
  max-width: 260px;
  margin: 0;
  color: #62759d;
  font-size: 16px;
  font-weight: 600;
  line-height: 1.65;
}

.big-illustration {
  position: absolute;
  right: 0;
  bottom: 16px;
  left: 0;
  display: grid;
  place-items: center;
  pointer-events: none;
}

.big-illustration svg {
  width: min(94%, 330px);
  height: auto;
  filter: drop-shadow(0 10px 8px rgba(95,97,205,.12));
}

.clipboard-art {
  bottom: 30px;
}

.small-illustration {
  position: absolute;
  right: 10px;
  bottom: 10px;
  width: 40%;
  max-width: 160px;
  pointer-events: none;
}

.small-illustration svg {
  display: block;
  width: 100%;
  height: auto;
  filter: drop-shadow(0 7px 8px rgba(95,97,160,.1));
}

.identity-art {
  right: 12px;
  bottom: 8px;
}

.star-art {
  right: 8px;
  bottom: 8px;
}

.laptop-art {
  right: 8%;
  bottom: 4px;
  width: 37%;
  max-width: 220px;
}

.featured-footer {
  position: absolute;
  bottom: 22px;
  left: 26px;
  display: flex;
  align-items: center;
  gap: 8px;
  color: #7772cf;
  font-size: 13px;
  font-weight: 800;
}

.mini-dot {
  width: 9px;
  height: 9px;
  border-radius: 50%;
  background: #8c78ff;
  box-shadow: 0 0 0 5px rgba(140,120,255,.13);
}

/* Daftar tugas yang benar-benar interaktif */

.live-section {
  margin-top: 30px;
  padding: 28px;
  border: 1px solid rgba(255,255,255,.95);
  border-radius: 29px;
  background: rgba(255,255,255,.68);
  box-shadow:
    10px 14px 30px rgba(101,125,190,.1),
    inset 2px 2px 5px rgba(255,255,255,.95);
  backdrop-filter: blur(12px);
}

.section-heading {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 15px;
  margin-bottom: 20px;
}

.eyebrow {
  color: #8584d9;
  font-size: 11px;
  font-weight: 900;
  letter-spacing: 2px;
}

.section-heading h2 {
  margin: 3px 0 0;
  color: #1b2b4e;
  font-size: 28px;
  font-weight: 900;
}

.task-count {
  padding: 9px 15px;
  border: 1px solid #e4e7ff;
  border-radius: 999px;
  color: #6867df;
  background: #f0efff;
  font-size: 13px;
  font-weight: 800;
}

.empty-state {
  padding: 35px 15px;
  border: 2px dashed #e0e5fa;
  border-radius: 23px;
  text-align: center;
  background: rgba(246,248,255,.65);
}

.empty-icon {
  display: grid;
  place-items: center;
  width: 55px;
  height: 55px;
  margin: 0 auto 12px;
  border-radius: 18px;
  color: #786cf2;
  background: #ebe8ff;
  font-size: 27px;
  box-shadow: var(--empty-shadow, 4px 5px 12px rgba(110,110,190,.1));
}

.empty-state h3 {
  margin: 0;
  color: #263758;
  font-size: 19px;
  font-weight: 900;
}

.empty-state p {
  margin: 6px 0 0;
  color: #7d8db0;
  font-size: 14px;
  font-weight: 600;
}

.live-list {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 15px;
  margin: 0;
  padding: 0;
  list-style: none;
}

.live-item {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 14px;
  min-width: 0;
  padding: 17px 18px;
  border: 1px solid rgba(255,255,255,.95);
  border-radius: 21px;
  background: linear-gradient(145deg, #f0edff, #f8f7ff);
  box-shadow:
    7px 9px 18px rgba(108,128,181,.1),
    inset 2px 2px 4px rgba(255,255,255,.85);
  transition: transform .2s, box-shadow .2s;
}

.live-item:nth-child(4n + 2) {
  background: linear-gradient(145deg, #bd336a, #fff8fb);
}

.live-item:nth-child(4n + 3) {
  background: linear-gradient(145deg, #169bc4, #fffdf5);
}

.live-item:nth-child(4n + 4) {
  background: linear-gradient(145deg, #e9faf6, #f4fffc);
}

.live-item:hover {
  transform: translateY(-2px);
  box-shadow: 9px 12px 20px rgba(108,128,181,.13);
}

.task-label {
  display: flex;
  align-items: center;
  gap: 12px;
  min-width: 0;
  cursor: pointer;
}

.task-checkbox {
  width: 21px;
  height: 21px;
  flex-shrink: 0;
  margin: 0;
  accent-color: #7168f5;
  cursor: pointer;
}

.live-task-title {
  overflow-wrap: anywhere;
  color: #253858;
  font-size: 17px;
  font-weight: 800;
}

.live-item.completed .live-task-title {
  color: #929db7;
  text-decoration: line-through;
  text-decoration-thickness: 2px;
}

.delete-button {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 7px;
  flex-shrink: 0;
  padding: 9px 13px;
  border: 1px solid rgba(255,255,255,.95);
  border-radius: 999px;
  color: #f14d91;
  background: rgba(255,255,255,.8);
  box-shadow:
    4px 5px 10px rgba(156,110,169,.08),
    inset 1px 1px 3px white;
  font-size: 13px;
  font-weight: 800;
  cursor: pointer;
  transition: color .2s, background .2s, transform .2s;
}

.delete-button svg {
  width: 18px;
  height: 18px;
}

.delete-button:hover {
  transform: translateY(-1px);
  color: #d92d72;
  background: white;
}

.page-footer {
  padding: 24px 10px 5px;
  color: #8795b5;
  text-align: center;
  font-size: 13px;
  font-weight: 700;
}

.page-footer span {
  margin-right: 5px;
  color: #8a76f5;
}

/* Tablet */

@media (max-width: 1100px) {
  .taskify-page {
    padding: 22px;
  }

  .hero {
    align-items: stretch;
    flex-direction: column;
    gap: 22px;
  }

  .task-form {
    width: 100%;
  }

  .task-layout {
    grid-template-columns: repeat(2, minmax(0, 1fr));
    grid-template-rows: auto;
  }

  .featured-card {
    grid-row: auto;
    min-height: 380px;
  }

  .live-list {
    grid-template-columns: 1fr;
  }
}

/* HP */

@media (max-width: 600px) {
  .taskify-page {
    padding: 12px;
  }

  .hero {
    padding: 20px 16px;
    border-radius: 24px;
  }

  .brand {
    gap: 13px;
  }

  .brand-icon {
    width: 65px;
    height: 65px;
    padding: 12px;
    border-radius: 19px;
  }

  .brand-text h1 {
    font-size: 31px;
    letter-spacing: -1px;
  }

  .brand-text p {
    max-width: 240px;
    font-size: 12px;
    line-height: 1.6;
  }

  .task-form {
    flex-direction: column;
    align-items: stretch;
    gap: 12px;
  }

  .input-wrap {
    flex: auto;
    width: 100%;
    height: 55px;
    border-radius: 17px;
  }

  .add-button {
    width: 100%;
    min-height: 54px;
    border-radius: 17px;
  }

  .task-layout {
    grid-template-columns: 1fr;
    gap: 15px;
    margin-top: 16px;
  }

  .task-card {
    min-height: 210px;
    padding: 21px;
    border-radius: 24px;
  }

  .featured-card {
    min-height: 370px;
  }

  .task-card h2 {
    font-size: 25px;
  }

  .card-description {
    max-width: 60%;
    font-size: 14px;
  }

  .featured-card .card-description {
    max-width: 80%;
  }

  .big-illustration svg {
    width: 83%;
  }

  .small-illustration {
    width: 36%;
  }

  .live-section {
    margin-top: 18px;
    padding: 19px 14px;
    border-radius: 23px;
  }

  .section-heading h2 {
    font-size: 23px;
  }

  .live-item {
    padding: 14px 12px;
    border-radius: 18px;
  }

  .live-task-title {
    font-size: 15px;
  }

  .delete-button {
    padding: 8px 10px;
    font-size: 12px;
  }

  .page-footer {
    font-size: 11px;
    line-height: 1.7;
  }
}
</style>
