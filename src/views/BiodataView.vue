<template>
  <div class="biodata-container">
    <div class="cv-wrapper">
      <header class="cv-header">
        <div class="profile-section">
          <div class="profile-image">
            <img src="@/assets/profile-photo.png" alt="Foto Profil" />
          </div>
          <div class="profile-info">
            <h1>{{ biodata.nama }}</h1>
            <h2>{{ biodata.profesi }}</h2>
            <p>{{ biodata.deskripsi }}</p>
          </div>
        </div>
      </header>

      <main class="cv-content">
        <section class="contact-info">
          <h3>Informasi Kontak</h3>
          <div class="contact-item">
            <strong>Email:</strong> {{ biodata.email }}
          </div>
          <div class="contact-item">
            <strong>Telepon:</strong> {{ biodata.telepon }}
          </div>
          <div class="contact-item">
            <strong>Alamat:</strong> {{ biodata.alamat }}
          </div>
          <div class="contact-item">
            <strong>LinkedIn:</strong> {{ biodata.linkedin }}
          </div>
        </section>

        <section class="education">
          <h3>Pendidikan</h3>
          <div v-for="edu in biodata.pendidikan" :key="edu.id" class="education-item">
            <h4>{{ edu.institusi }}</h4>
            <p><strong>{{ edu.jurusan }}</strong></p>
            <p>{{ edu.tahun }}</p>
          </div>
        </section>

        <section class="experience">
          <h3>Pengalaman</h3>
          <div v-for="exp in biodata.pengalaman" :key="exp.id" class="experience-item">
            <h4>{{ exp.posisi }}</h4>
            <p><strong>{{ exp.perusahaan }}</strong></p>
            <p>{{ exp.periode }}</p>
            <ul>
              <li v-for="desc in exp.deskripsi" :key="desc">{{ desc }}</li>
            </ul>
          </div>
        </section>

        <section class="skills">
          <h3>Keahlian</h3>
          <div class="skills-grid">
            <div v-for="skill in biodata.keahlian" :key="skill.kategori" class="skill-category">
              <h4>{{ skill.kategori }}</h4>
              <ul>
                <li v-for="item in skill.items" :key="item">{{ item }}</li>
              </ul>
            </div>
          </div>
        </section>
      </main>
    </div>
  </div>
</template>

<script setup>
defineOptions({ name: 'UserBiodata' })
import { ref } from 'vue'

const biodata = ref({
  nama: 'Rino Oktavian Ridwan',
  profesi: 'Software Engineer',
  deskripsi: 'Software Engineer berpengalaman dengan spesialisasi dalam pengembangan aplikasi web menggunakan Vue.js, React, dan Node.js.',
  email: 'rinooktavianridwan@email.com',
  telepon: '+62 123-4567-8901',
  alamat: 'Malang, Indonesia',
  linkedin: 'www.linkedin.com/in/rino-oktavian-ridwan',
  pendidikan: [
    {
      id: 1,
      institusi: 'Universitas Brawijaya',
      jurusan: 'Teknik Informatika',
      tahun: '2022 - 2025',
    },
    {
      id: 2,
      institusi: 'SMA Negeri 1 Magetan',
      jurusan: 'IPA',
      tahun: '2015 - 2018',
    }
  ],
  pengalaman: [
    {
      id: 1,
      posisi: 'Anggota Frontend Developer POROS UB',
      perusahaan: 'POROS Universitas Brawijaya',
      periode: '2024 - 2025',
      deskripsi: [
        'Mengembangkan web menggunakan Next.js',
      ]
    },
    {
      id: 2,
      posisi: 'Anggota DevOps POROS UB',
      perusahaan: 'POROS Universitas Brawijaya',
      periode: '2025 - Sekarang',
      deskripsi: [
        'Berkolaborasi dengan tim DevOps dalam study group',
      ]
    }
  ],
  keahlian: [
    {
      kategori: 'Frontend',
      items: ['Vue.js', 'React.js', 'Next.js', 'HTML5', 'CSS3', 'Tailwind CSS']
    },
    {
      kategori: 'Backend',
      items: ['Node.js', 'Express.js', 'Laravel']
    },
    {
      kategori: 'Database',
      items: ['MySQL', 'MongoDB']
    },
    {
      kategori: 'Tools',
      items: ['Git', 'Docker', 'VS Code', 'Postman', 'VPS']
    }
  ],
})
</script>

<style scoped>
.biodata-container {
  max-width: 100vw;
  max-height: 100vh;
  overflow-y: auto;
  padding: 1rem;
  background: var(--color-background);
  color: var(--color-text);
}

.cv-wrapper {
  max-width: 900px;
  margin: 0 auto;
  background: var(--color-background-soft);
  border-radius: 12px;
  padding: 2rem;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  border: 1px solid var(--color-border);
}

.cv-header {
  border-bottom: 2px solid var(--color-border);
  padding-bottom: 2rem;
  margin-bottom: 2rem;
}

.profile-section {
  display: flex;
  gap: 2rem;
  align-items: center;
}

.profile-image {
  flex-shrink: 0;
}

.profile-image img {
  width: 150px;
  height: 150px;
  border-radius: 50%;
  object-fit: cover;
  border: 3px solid hsla(160, 100%, 37%, 1);
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

.profile-info h1 {
  font-size: 2rem;
  margin: 0 0 0.5rem 0;
  color: var(--color-heading);
  font-weight: 600;
}

.profile-info h2 {
  font-size: 1.5rem;
  color: hsla(160, 100%, 37%, 1);
  margin: 0 0 1rem 0;
  font-weight: 500;
}

.profile-info p {
  color: var(--color-text);
  line-height: 1.6;
  margin: 0;
}

.cv-content section {
  margin-bottom: 2.5rem;
}

.cv-content h3 {
  font-size: 1.5rem;
  color: var(--color-heading);
  border-bottom: 2px solid hsla(160, 100%, 37%, 1);
  padding-bottom: 0.5rem;
  margin-bottom: 1.5rem;
  font-weight: 600;
}

.contact-info {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 1rem;
  background: var(--color-background-mute);
  padding: 1.5rem;
  border-radius: 8px;
  border: 1px solid var(--color-border);
}

.contact-item {
  padding: 0.5rem 0;
  color: var(--color-text);
}

.contact-item strong {
  color: var(--color-heading);
}

.education-item,
.experience-item {
  margin-bottom: 1.5rem;
  padding: 1.5rem;
  border-left: 4px solid hsla(160, 100%, 37%, 1);
  background: var(--color-background-mute);
  border-radius: 0 8px 8px 0;
  border: 1px solid var(--color-border);
  border-left: 4px solid hsla(160, 100%, 37%, 1);
}

.education-item h4,
.experience-item h4 {
  color: var(--color-heading);
  margin-bottom: 0.5rem;
  font-weight: 600;
  font-size: 1.2rem;
}

.education-item p,
.experience-item p {
  color: var(--color-text);
  margin: 0.25rem 0;
}

.experience-item ul {
  margin-top: 0.75rem;
  padding-left: 1.5rem;
  color: var(--color-text);
}

.experience-item li {
  margin-bottom: 0.5rem;
  line-height: 1.5;
}

.skills-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 1.5rem;
}

.skill-category {
  background: var(--color-background-mute);
  padding: 1.5rem;
  border-radius: 8px;
  border: 1px solid var(--color-border);
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.skill-category:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
}

.skill-category h4 {
  color: hsla(160, 100%, 37%, 1);
  margin-bottom: 1rem;
  font-weight: 600;
  font-size: 1.1rem;
}

.skill-category ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.skill-category li {
  padding: 0.4rem 0;
  border-bottom: 1px solid var(--color-border);
  color: var(--color-text);
  font-size: 0.95rem;
}

.skill-category li:last-child {
  border-bottom: none;
}

.achievements {
  background: var(--color-background-mute);
  padding: 1.5rem;
  border-radius: 8px;
  border: 1px solid var(--color-border);
}

.achievements h3 {
  margin-top: 0;
}

.achievements ul {
  columns: 2;
  column-gap: 2rem;
  margin: 0;
  padding: 0;
  list-style: none;
}

.achievements li {
  margin-bottom: 0.75rem;
  break-inside: avoid;
  color: var(--color-text);
  padding-left: 1rem;
  position: relative;
}

.achievements li::before {
  content: '•';
  color: hsla(160, 100%, 37%, 1);
  position: absolute;
  left: 0;
  font-weight: bold;
}

/* Responsive Design */
@media (max-width: 768px) {
  .biodata-container {
    padding: 0.5rem;
  }

  .cv-wrapper {
    padding: 1.5rem;
    margin: 0;
    border-radius: 8px;
  }

  .profile-section {
    flex-direction: column;
    text-align: center;
    gap: 1.5rem;
  }

  .profile-image img {
    width: 120px;
    height: 120px;
  }

  .profile-info h1 {
    font-size: 2rem;
  }

  .profile-info h2 {
    font-size: 1.3rem;
  }

  .contact-info {
    grid-template-columns: 1fr;
    padding: 1rem;
  }

  .skills-grid {
    grid-template-columns: 1fr;
  }

  .achievements ul {
    columns: 1;
  }

  .cv-content h3 {
    font-size: 1.3rem;
  }
}

@media (max-width: 480px) {
  .cv-wrapper {
    padding: 1rem;
  }

  .profile-info h1 {
    font-size: 1.8rem;
  }

  .profile-info h2 {
    font-size: 1.2rem;
  }

  .education-item,
  .experience-item,
  .skill-category,
  .contact-info,
  .achievements {
    padding: 1rem;
  }
}

/* Smooth scrolling */
.biodata-container {
  scroll-behavior: smooth;
}

/* Custom scrollbar for webkit browsers */
.biodata-container::-webkit-scrollbar {
  width: 8px;
}

.biodata-container::-webkit-scrollbar-track {
  background: var(--color-background-soft);
}

.biodata-container::-webkit-scrollbar-thumb {
  background: var(--color-border);
  border-radius: 4px;
}

.biodata-container::-webkit-scrollbar-thumb:hover {
  background: var(--color-border-hover);
}
</style>
