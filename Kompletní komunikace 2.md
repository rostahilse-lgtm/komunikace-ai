# 🏗️ KOMPLETNÍ PROJEKT - EVIDENCE PRÁCE 2026
# Všechny soubory v jednom dokumentu pro snadné čtení AI

**Datum vytvoření:** 17.01.2026  
**Poslední update:** 17.01.2026  
**Autor:** rostahilse-lgtm  
**AI asistent:** Claude (Anthropic)  
**Repository:** https://github.com/rostahilse-lgtm/evidence-prace  
**Live Demo:** https://evidence-prace.vercel.app

---

## 📑 OBSAH - RYCHLÁ NAVIGACE

### Hlavní soubory
- [1️⃣ index.html - HTML struktura](#1️⃣-indexhtml)
- [2️⃣ styles.css - Stylování](#2️⃣-stylescss)

### JavaScript - Utility
- [3️⃣ js/config.js - Konfigurace](#3️⃣-jsconfigjs)
- [4️⃣ js/utils.js - Pomocné funkce](#4️⃣-jsutilsjs)
- [5️⃣ js/api.js - API komunikace](#5️⃣-jsapijs)
- [6️⃣ js/main.js - Hlavní aplikace](#6️⃣-jsmainjs)

### JavaScript - Komponenty
- [7️⃣ js/components/login.js - Přihlášení](#7️⃣-jscomponentsloginjs)
- [8️⃣ js/components/home.js - Domovská stránka](#8️⃣-jscomponentshomejs)
- [9️⃣ js/components/summary.js - Přehledy](#9️⃣-jscomponentssummaryjs)
- [🔟 js/components/settings.js - Nastavení](#🔟-jscomponentssettingsjs)

### JavaScript - Admin komponenty
- [1️⃣1️⃣ js/components/admin/worker-detail.js - Detail pracovníka](#1️⃣1️⃣-jscomponentsadminworker-detailjs)
- [1️⃣2️⃣ js/components/admin/day-view.js - Přehled dne](#1️⃣2️⃣-jscomponentsadminday-viewjs)
- [1️⃣3️⃣ js/components/admin/admin.js - Admin panel](#1️⃣3️⃣-jscomponentsadminadminjs)

### Dodatečné informace
- [📊 Statistiky projektu](#📊-statistiky-projektu)
- [🐛 Známé problémy](#🐛-známé-problémy)
- [🔧 Technologie](#🔧-technologie)

---

# 1️⃣ index.html

**Popis:** Hlavní HTML soubor aplikace  
**Cesta:** `/index.html`  
**Velikost:** ~1.5 KB

```html
<!DOCTYPE html>
<html lang="cs">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width,initial-scale=1">
  <title>Evidence práce 2026</title>
  <link href="https://fonts.googleapis.com/css?family=Material+Icons" rel="stylesheet">
  <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@100;300;400;500;700;900&display=swap" rel="stylesheet">
  <link href="https://cdn.jsdelivr.net/npm/quasar@2.12.0/dist/quasar.prod.css" rel="stylesheet">
  <link href="styles.css" rel="stylesheet">
</head>
<body>
  <!-- Jen prázdný div - vše se renderuje z main.js -->
  <div id="app"></div>

  <!-- 1. KNIHOVNY -->
  <script src="https://cdn.jsdelivr.net/npm/vue@3.3.4/dist/vue.global.prod.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/quasar@2.12.0/dist/quasar.umd.prod.js"></script>

  <!-- 2. UTILITY -->
  <script src="js/config.js"></script>
  <script src="js/utils.js"></script>
  <script src="js/api.js"></script>

  <!-- 3. MAIN (vytvoří app) -->
  <script src="js/main.js"></script>

  <!-- 4. KOMPONENTY -->
  <script src="js/components/login.js"></script>
  <script src="js/components/home.js"></script>
  <script src="js/components/summary.js"></script>
  <script src="js/components/settings.js"></script>
  <script src="js/components/admin/worker-detail.js"></script>
  <script src="js/components/admin/day-view.js"></script>
  <script src="js/components/admin/admin.js"></script>
</body>
</html>
```

---

# 2️⃣ styles.css

**Popis:** Všechny CSS styly aplikace  
**Cesta:** `/styles.css`  
**Velikost:** ~2 KB

```css
* { box-sizing: border-box; } 
body { margin: 0; padding: 0; font-family: 'Roboto', sans-serif; background: #f5f5f5; } 
.login-container { display: flex; justify-content: center; align-items: center; min-height: 100vh; background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); } 
.login-card { background: white; padding: 2rem; border-radius: 1rem; box-shadow: 0 10px 30px rgba(0,0,0,0.3); width: 90%; max-width: 400px; } 
.tab-content { padding: 1rem; padding-bottom: 80px; } 
.record-card { background: white; border-radius: 8px; margin-bottom: 12px; padding: 12px; border-left: 4px solid #1976D2; box-shadow: 0 2px 4px rgba(0,0,0,0.1); } 
.time-btn { font-size: 1.1rem; padding: 1rem; } 
.summary-box { background: #e3f2fd; padding: 1rem; border-radius: 8px; margin: 1rem 0; border-left: 4px solid #1976D2; } 
.summary-item { display: flex; justify-content: space-between; margin: 0.5rem 0; font-size: 1.1rem; } 
.summary-label { font-weight: 500; } 
.summary-value { font-weight: bold; color: #1976D2; } 
.note-display { background: #e8f5e9; padding: 0.75rem; border-radius: 4px; margin-top: 0.5rem; border-left: 3px solid #4caf50; } 
.admin-badge { background: #ff9800; color: white; padding: 4px 12px; border-radius: 12px; font-size: 0.85rem; font-weight: bold; } 
.worker-card { background: white; border-radius: 8px; padding: 16px; margin-bottom: 12px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); cursor: pointer; transition: all 0.3s; } 
.worker-card:hover { box-shadow: 0 4px 12px rgba(0,0,0,0.2); transform: translateY(-2px); } 
.balance-positive { color: #4caf50; font-weight: bold; } 
.balance-negative { color: #f44336; font-weight: bold; } 
.date-filter-box { background: #fff3e0; padding: 1rem; border-radius: 8px; margin: 1rem 0; border-left: 4px solid #ff9800; } 
.edit-icon { cursor: pointer; color: #1976D2; } 
.edit-icon:hover { color: #0d47a1; }
```

---

# 3️⃣ js/config.js

**Popis:** Konfigurace API  
**Cesta:** `/js/config.js`  
**Velikost:** ~150 bytes

```javascript
const DEFAULT_API_URL = 'https://script.google.com/macros/s/AKfycbxHKXslWtYaQ7FbJot2PvxcqQSDtjNjCK8-AS63xwdpvnG8qVZfT1j354IIw53llk9v/exec';
```

---

# 4️⃣ js/utils.js

**Popis:** Pomocné funkce pro formátování datumů a časů  
**Cesta:** `/js/utils.js`  
**Velikost:** ~1.5 KB

```javascript
function formatTime(timestamp) { 
  return new Date(timestamp).toLocaleString('cs-CZ', { hour: '2-digit', minute: '2-digit' }); 
} 
 
function formatShortDateTime(timestamp) { 
  const d = new Date(timestamp); 
  return `${d.getDate()}.${d.getMonth() + 1}.${d.getFullYear()} ${String(d.getHours()).padStart(2, '0')}:${String(d.getMinutes()).padStart(2, '0')}`; 
} 
 
function formatTimeRange(timeFr, timeTo) { 
  const d1 = new Date(timeFr); 
  const d2 = new Date(timeTo); 
  return `${d1.getDate()}.${d1.getMonth() + 1}. ${String(d1.getHours()).padStart(2, '0')}:${String(d1.getMinutes()).padStart(2, '0')} - ${String(d2.getHours()).padStart(2, '0')}:${String(d2.getMinutes()).padStart(2, '0')}`; 
} 
 
function getTodayDate() { 
  const today = new Date(); 
  return `${String(today.getDate()).padStart(2, '0')}. ${String(today.getMonth() + 1).padStart(2, '0')}. ${today.getFullYear()}`; 
} 
 
function getMonthStart() { 
  const today = new Date(); 
  return `01. ${String(today.getMonth() + 1).padStart(2, '0')}. ${today.getFullYear()}`; 
} 
 
function parseDateString(dateStr) { 
  const parts = dateStr.split('. '); 
  return new Date(parts[2], parts[1] - 1, parts[0]); 
} 
 
function formatDateForInput(dateStr) { 
  const date = parseDateString(dateStr); 
  return date.toISOString().split('T')[0]; 
} 
 
function formatDateFromInput(inputDate) { 
  const date = new Date(inputDate); 
  return `${String(date.getDate()).padStart(2, '0')}. ${String(date.getMonth() + 1).padStart(2, '0')}. ${date.getFullYear()}`; 
}
```

---

# 5️⃣ js/api.js

**Popis:** API komunikace s Google Apps Script  
**Cesta:** `/js/api.js`  
**Velikost:** ~800 bytes

```javascript
async function apiCall(action, params = {}) { 
  const apiUrl = localStorage.getItem('apiUrl') || DEFAULT_API_URL; 
  const url = new URL(apiUrl); 
  url.searchParams.append('action', action); 
   
  Object.keys(params).forEach(key => { 
    if (params[key] !== null && params[key] !== undefined) { 
      url.searchParams.append(key, params[key]); 
    } 
  }); 
   
  try { 
    const response = await fetch(url); 
    const data = await response.json(); 
     
    // Přidat success flag pro kompatibilitu 
    if (data.code === '000') { 
      data.success = true; 
    } else { 
      data.success = false; 
    } 
     
    return data; 
  } catch (error) { 
    return {  
      code: '999',  
      error: 'Chyba připojení: ' + error.message, 
      success: false, 
      data: null 
    }; 
  } 
}
```

---

# 6️⃣ js/main.js

**Popis:** Hlavní Vue aplikace  
**Cesta:** `/js/main.js`  
**Velikost:** ~5 KB

```javascript
// Vytvoření Vue aplikace 
window.app = Vue.createApp({ 
  data() { 
    return { 
      isLoggedIn: false, 
      currentUser: null, 
      isAdmin: false, 
      currentView: 'home', 
      loading: false, 
      message: '', 
      showMessageDialog: false, 
      contracts: [], 
      jobs: [], 
      summary: { totalEarnings: 0, totalPaid: 0, balance: 0 }, 
      records: [], 
      advances: [], 
      lunches: [], 
      allSummary: [], 
      allRecords: [], 
      allAdvances: [] 
    } 
  }, 
 
  methods: { 
    showMessage(msg) { 
      this.message = msg; 
      this.showMessageDialog = true; 
      setTimeout(() => { 
        this.message = ''; 
        this.showMessageDialog = false; 
      }, 4000); 
    }, 
     
    async handleLogin(worker) { 
      this.currentUser = { 
        id: worker[0], 
        name: worker[1], 
        active: worker[2] === 'Y', 
        admin: worker[3] === 'Y' 
      }; 
      this.isLoggedIn = true; 
      this.isAdmin = this.currentUser.admin; 
      localStorage.setItem('workerId', this.currentUser.id); 
      await this.loadUserData(); 
      if (this.isAdmin) await this.loadAdminData(); 
      this.showMessage('Přihlášen: ' + this.currentUser.name); 
    }, 
     
    async loadUserData() { 
      this.loading = true; 
      const [c, j, s, r, a] = await Promise.all([ 
        apiCall('get', { type: 'contracts' }), 
        apiCall('get', { type: 'jobs' }), 
        apiCall('getsummary', { id_worker: this.currentUser.id }), 
        apiCall('getrecords', { id_worker: this.currentUser.id }), 
        apiCall('getadvances', { id_worker: this.currentUser.id }) 
      ]); 
      if (c.data) this.contracts = c.data; 
      if (j.data) this.jobs = j.data; 
      if (s.data) this.summary = s.data; 
      if (r.data) this.records = r.data; 
      if (a.data) { 
        this.advances = a.data.filter(adv => adv[5] !== 'oběd'); 
        this.lunches = a.data.filter(adv => adv[5] === 'oběd'); 
      } 
      this.loading = false; 
    }, 
     
    async loadAdminData() { 
      this.loading = true; 
      const [summary, records, advances] = await Promise.all([ 
        apiCall('getallsummary'), 
        apiCall('getallrecords'), 
        apiCall('getalladvances') 
      ]); 
      if (summary.data) this.allSummary = summary.data; 
      if (records.data) this.allRecords = records.data; 
      if (advances.data) this.allAdvances = advances.data; 
      this.loading = false; 
    }, 
     
    logout() { 
      this.isLoggedIn = false; 
      this.currentUser = null; 
      this.isAdmin = false; 
      localStorage.removeItem('workerId'); 
      this.showMessage('Odhlášen'); 
    } 
  }, 
   
  async mounted() { 
    const savedId = localStorage.getItem('workerId'); 
    if (savedId) { 
      this.loading = true; 
      const res = await apiCall('get', { type: 'workers' }); 
      if (res.code === '000' && res.data) { 
        const worker = res.data.find(w => String(w[0]) === String(savedId)); 
        if (worker) await this.handleLogin(worker); 
        else localStorage.removeItem('workerId'); 
      } 
      this.loading = false; 
    } 
  }, 
 
  template: ` 
    <q-layout view="hHh lpR fFf"> 
      <q-header v-if="isLoggedIn" class="bg-primary text-white"> 
        <q-toolbar> 
          <q-toolbar-title>{{ currentUser.name }}</q-toolbar-title> 
          <span v-if="isAdmin" class="admin-badge q-ml-sm">ADMIN</span> 
          <q-btn flat round dense icon="logout" @click="logout" /> 
        </q-toolbar> 
      </q-header> 
 
      <q-page-container> 
        <q-page padding> 
          <div v-if="loading" class="flex flex-center q-pa-xl"> 
            <q-spinner color="primary" size="3em" /> 
          </div> 
 
          <login-component  
            v-if="!isLoggedIn && !loading" 
            :loading="loading" 
            @login="handleLogin" 
            @message="showMessage" 
          /> 
 
          <home-component 
            v-if="isLoggedIn && currentView === 'home' && !loading" 
            :current-user="currentUser" 
            :contracts="contracts" 
            :jobs="jobs" 
            :loading="loading" 
            @message="showMessage" 
            @reload="loadUserData" 
          /> 
 
          <summary-component 
            v-if="isLoggedIn && currentView === 'summary' && !loading" 
            :summary="summary" 
            :records="records" 
            :advances="advances" 
            :lunches="lunches" 
          /> 
 
          <admin-component 
            v-if="isLoggedIn && isAdmin && currentView === 'admin' && !loading" 
            :all-summary="allSummary" 
            :all-records="allRecords" 
            :all-advances="allAdvances" 
            :contracts="contracts" 
            :jobs="jobs" 
            :loading="loading" 
            @message="showMessage" 
            @reload="loadAdminData" 
          /> 
 
          <settings-component 
            v-if="isLoggedIn && currentView === 'settings' && !loading" 
            @message="showMessage" 
          /> 
        </q-page> 
      </q-page-container> 
 
      <q-footer v-if="isLoggedIn" class="bg-white text-grey-8"> 
        <q-tabs v-model="currentView" dense align="justify" active-color="primary"> 
          <q-tab name="home" icon="home" label="Domů" /> 
          <q-tab name="summary" icon="assessment" label="Přehledy" /> 
          <q-tab v-if="isAdmin" name="admin" icon="admin_panel_settings" label="Admin" /> 
          <q-tab name="settings" icon="settings" label="Nastavení" /> 
        </q-tabs> 
      </q-footer> 
 
      <q-dialog v-model="showMessageDialog" position="bottom"> 
        <q-card style="width: 350px"> 
          <q-card-section>{{ message }}</q-card-section> 
        </q-card> 
      </q-dialog> 
    </q-layout> 
  ` 
}); 
 
// Inicializace až po načtení všech komponent 
setTimeout(() => { 
  window.app.use(Quasar); 
  window.app.mount('#app'); 
}, 100);
```

---

# 7️⃣ js/components/login.js

**Popis:** Komponenta přihlášení  
**Cesta:** `/js/components/login.js`  
**Velikost:** ~1 KB

```javascript
app.component('login-component', {
  props: ['loading'],
  emits: ['login', 'message'],
  
  data() {
    return {
      loginCode: ''
    }
  },
  
  methods: {
    async handleLogin() {
      if (!this.loginCode) {
        this.$emit('message', 'Zadejte kód pracovníka');
        return;
      }
      
      const res = await apiCall('get', { type: 'workers' });
      
      if (res.code === '000' && res.data) {
        const worker = res.data.find(w => String(w[0]) === String(this.loginCode));
        
        if (worker) {
          this.$emit('login', worker);
        } else {
          this.$emit('message', 'Neplatný kód pracovníka');
        }
      } else {
        this.$emit('message', 'Chyba: ' + (res.error || 'Nepodařilo se načíst data'));
      }
    }
  },
  
  template: `
    <div class="login-container">
      <div class="login-card">
        <h1 style="text-align: center; color: #1976D2; margin-bottom: 2rem;">
          Evidence práce 2026
        </h1>
        <q-input 
          v-model="loginCode" 
          label="Kód pracovníka" 
          type="number" 
          outlined 
          @keyup.enter="handleLogin" 
          class="q-mb-md"
        />
        <q-btn 
          @click="handleLogin" 
          label="Přihlásit" 
          color="primary" 
          :loading="loading" 
          class="full-width q-mt-md" 
          size="lg"
        />
      </div>
    </div>
  `
});
```

---

# 8️⃣ js/components/home.js

**Popis:** Komponenta domovské stránky (Směna, Oběd, Záloha) - AKTUÁLNÍ NEFUNKČNÍ VERZE  
**Cesta:** `/js/components/home.js`  
**Velikost:** ~7 KB  
**⚠️ STAV:** Obsahuje chyby - aplikace se načítá ale nefunguje

```javascript
// Komponenta pro domovskou stránku (Směna, Oběd, Záloha)
app.component('home-component', {
  props: ['currentUser', 'contracts', 'jobs', 'loading'],
  emits: ['message', 'reload'],
  
  data() {
    return {
      currentTab: 'shift',
      
      // Formulář směny - PŮVODNÍ LOGIKA
      shiftForm: {
        contractId: null,
        jobId: null,
        timeStart: null,
        timeEnd: null,
        note: ''
      },
      
      // Formulář zálohy
      advanceForm: {
        amount: null,
        reason: ''
      }
    }
  },
  
  computed: {
    contractOptions() {
      return this.contracts.map(c => ({ label: `${c[0]} - ${c[1]}`, value: c[0] }));
    },
    jobOptions() {
      return this.jobs.map(j => ({ label: j[1], value: j[0] }));
    }
  },
  
  methods: {
    // === SMĚNA - PŮVODNÍ LOGIKA ===
    
    setArrival() {
      this.shiftForm.timeStart = Date.now();
      this.saveShiftState();
      this.$emit('message', 'Příchod: ' + formatTime(this.shiftForm.timeStart));
    },
    
    setDeparture() {
      if (!this.shiftForm.timeStart) {
        this.$emit('message', 'Nejdříve zaznamenejte příchod');
        return;
      }
      this.shiftForm.timeEnd = Date.now();
      this.saveShiftState();
      this.$emit('message', 'Odchod: ' + formatTime(this.shiftForm.timeEnd));
    },
    
    async saveShift() {
      // VALIDACE - PŮVODNÍ
      if (!this.shiftForm.contractId || !this.shiftForm.jobId || !this.shiftForm.timeStart || !this.shiftForm.timeEnd) {
        this.$emit('message', 'Vyplňte všechna pole');
        return;
      }
      
      // VALIDACE POZNÁMKY - TOTO CHYBĚLO!
      if (!this.shiftForm.note || this.shiftForm.note.trim() === '') {
        this.$emit('message', 'Poznámka je povinná');
        return;
      }
      
      try {
        const res = await apiCall('saverecord', {
          id_contract: this.shiftForm.contractId,
          id_worker: this.currentUser.id,
          id_job: this.shiftForm.jobId,
          time_fr: this.shiftForm.timeStart,
          time_to: this.shiftForm.timeEnd,
          note: this.shiftForm.note
        });
        
        if (res.code === '000') {
          this.$emit('message', '✓ Směna uložena');
          this.clearShiftState();
          this.$emit('reload');
        } else {
          this.$emit('message', 'Chyba: ' + res.error);
        }
      } catch (error) {
        console.error('Save shift error:', error);
        this.$emit('message', 'Chyba při ukládání směny');
      }
    },
    
    // === LOCALSTORAGE - PŮVODNÍ LOGIKA ===
    
    saveShiftState() {
      const state = {
        timeStart: this.shiftForm.timeStart,
        timeEnd: this.shiftForm.timeEnd,
        contractId: this.shiftForm.contractId,
        jobId: this.shiftForm.jobId,
        note: this.shiftForm.note,
        date: getTodayDate()
      };
      localStorage.setItem('shiftState_' + this.currentUser.id, JSON.stringify(state));
    },
    
    loadShiftState() {
      const saved = localStorage.getItem('shiftState_' + this.currentUser.id);
      if (saved) {
        const state = JSON.parse(saved);
        if (state.date === getTodayDate()) {
          this.shiftForm.timeStart = state.timeStart;
          this.shiftForm.timeEnd = state.timeEnd;
          this.shiftForm.contractId = state.contractId;
          this.shiftForm.jobId = state.jobId;
          this.shiftForm.note = state.note;
        } else {
          this.clearShiftState();
        }
      }
    },
    
    clearShiftState() {
      localStorage.removeItem('shiftState_' + this.currentUser.id);
      this.shiftForm = {
        contractId: null,
        jobId: null,
        timeStart: null,
        timeEnd: null,
        note: ''
      };
    },
    
    // === OBĚD - PŮVODNÍ LOGIKA ===
    
    async saveLunch() {
      try {
        const res = await apiCall('savelunch', {
          id_worker: this.currentUser.id,
          name_worker: this.currentUser.name,
          time: Date.now()
        });
        
        if (res.code === '000') {
          this.$emit('message', '✓ Oběd uložen');
          this.$emit('reload');
        } else {
          this.$emit('message', 'Chyba: ' + res.error);
        }
      } catch (error) {
        console.error('Save lunch error:', error);
        this.$emit('message', 'Chyba při ukládání oběda');
      }
    },
    
    // === ZÁLOHA - PŮVODNÍ LOGIKA ===
    
    async saveAdvance() {
      if (!this.advanceForm.amount || !this.advanceForm.reason) {
        this.$emit('message', 'Vyplňte částku a důvod');
        return;
      }
      
      try {
        const res = await apiCall('saveadvance', {
          id_worker: this.currentUser.id,
          name_worker: this.currentUser.name,
          time: Date.now(),
          payment: this.advanceForm.amount,
          payment_reason: this.advanceForm.reason
        });
        
        if (res.code === '000') {
          this.$emit('message', '✓ Záloha uložena');
          this.advanceForm.amount = null;
          this.advanceForm.reason = '';
          this.$emit('reload');
        } else {
          this.$emit('message', 'Chyba: ' + res.error);
        }
      } catch (error) {
        console.error('Save advance error:', error);
        this.$emit('message', 'Chyba při ukládání zálohy');
      }
    }
  },
  
  // === WATCH - PŮVODNÍ LOGIKA ===
  watch: {
    'shiftForm.contractId'() { this.saveShiftState(); },
    'shiftForm.jobId'() { this.saveShiftState(); },
    'shiftForm.note'() { this.saveShiftState(); }
  },
  
  mounted() {
    this.loadShiftState();
  },
  
  // === TEMPLATE - PŮVODNÍ DESIGN ===
  template: `
    <div>
      <q-tabs v-model="currentTab" dense align="justify" class="text-primary">
        <q-tab name="shift" label="Směna"/>
        <q-tab name="lunch" label="Oběd"/>
        <q-tab name="advance" label="Záloha"/>
      </q-tabs>

      <!-- SMĚNA -->
      <div v-if="currentTab === 'shift'" class="q-pt-md">
        <q-btn 
          @click="setArrival" 
          color="green" 
          icon="login" 
          label="PŘÍCHOD" 
          class="full-width q-mb-md time-btn" 
          :disabled="shiftForm.timeStart"
        />
        
        <div v-if="shiftForm.timeStart" class="q-mb-md q-pa-sm" style="background: #e8f5e9; border-radius: 4px;">
          <div class="text-bold text-green-8">✓ Příchod zaznamenán</div>
          <div>{{ formatShortDateTime(shiftForm.timeStart) }}</div>
        </div>
        
        <q-btn 
          @click="setDeparture" 
          color="orange" 
          icon="logout" 
          label="ODCHOD" 
          class="full-width q-mb-md time-btn" 
          :disabled="!shiftForm.timeStart || shiftForm.timeEnd"
        />
        
        <div v-if="shiftForm.timeEnd" class="q-mb-md q-pa-sm" style="background: #fff3e0; border-radius: 4px;">
          <div class="text-bold text-orange-8">✓ Odchod zaznamenán</div>
          <div>{{ formatShortDateTime(shiftForm.timeEnd) }}</div>
          <div class="text-primary text-bold q-mt-sm">
            Odpracováno: {{ ((shiftForm.timeEnd - shiftForm.timeStart) / 3600000).toFixed(2) }} hod
          </div>
        </div>
        
        <q-select 
          v-model="shiftForm.contractId" 
          :options="contractOptions" 
          label="Zakázka *" 
          emit-value 
          map-options 
          outlined 
          class="q-mb-md"
        />
        
        <q-select 
          v-model="shiftForm.jobId" 
          :options="jobOptions" 
          label="Práce *" 
          emit-value 
          map-options 
          outlined 
          class="q-mb-md"
        />
        
        <q-input 
          v-model="shiftForm.note" 
          label="Poznámka *" 
          outlined 
          class="q-mb-md" 
          type="textarea" 
          rows="3"
        />
        
        <q-btn 
          @click="saveShift" 
          label="Uložit směnu" 
          color="primary" 
          :loading="loading" 
          class="full-width" 
          size="lg"
        />
      </div>

      <!-- OBĚD -->
      <div v-if="currentTab === 'lunch'" class="q-pt-md">
        <div class="text-center q-mb-md">
          <q-icon name="restaurant" size="4rem" color="orange"/>
          <div class="text-h6 q-mt-md">{{ getTodayDate() }}</div>
        </div>
        <q-btn 
          @click="saveLunch" 
          label="Uložit oběd" 
          color="orange" 
          :loading="loading" 
          class="full-width" 
          size="lg" 
          icon="restaurant"
        />
      </div>

      <!-- ZÁLOHA -->
      <div v-if="currentTab === 'advance'" class="q-pt-md">
        <q-input 
          v-model.number="advanceForm.amount" 
          label="Částka (Kč) *" 
          type="number" 
          outlined 
          class="q-mb-md"
        />
        <q-input 
          v-model="advanceForm.reason" 
          label="Důvod *" 
          outlined 
          class="q-mb-md" 
          type="textarea" 
          rows="2"
        />
        <q-btn 
          @click="saveAdvance" 
          label="Uložit zálohu" 
          color="primary" 
          :loading="loading" 
          class="full-width" 
          size="lg"
        />
      </div>
    </div>
  `
});
