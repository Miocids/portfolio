<script setup lang="ts">
interface Skill {
  name: string
  icon: string
  category: 'backend' | 'frontend' | 'tools'
}

const skills: Skill[] = [
  // Backend
  { name: 'Laravel', icon: '🔴', category: 'backend' },
  { name: 'PHP', icon: '🐘', category: 'backend' },
  { name: 'NestJS', icon: '🐈', category: 'backend' },
  { name: 'Node.js', icon: '🟢', category: 'backend' },
  { name: 'API REST', icon: '🔗', category: 'backend' },
  { name: 'MySQL', icon: '🗄️', category: 'backend' },
  
  // Frontend
  { name: 'Vue.js', icon: '💚', category: 'frontend' },
  { name: 'React', icon: '⚛️', category: 'frontend' },
  { name: 'Angular', icon: '🔺', category: 'frontend' },
  { name: 'TypeScript', icon: '📘', category: 'frontend' },
  { name: 'JavaScript', icon: '💛', category: 'frontend' },
  { name: 'Ionic', icon: '📱', category: 'frontend' },
  
  // Tools
  { name: 'Filament', icon: '🎨', category: 'tools' },
  { name: 'n8n', icon: '⚙️', category: 'tools' },
  { name: 'Git', icon: '📦', category: 'tools' },
  { name: 'Docker', icon: '🐳', category: 'tools' },
]

const categories = [
  { id: 'backend', label: 'Backend & Cloud', color: 'var(--primary)' },
  { id: 'frontend', label: 'Frontend & UI', color: 'var(--secondary)' },
  { id: 'tools', label: 'Herramientas & DevOps', color: '#8b5cf6' },
]

const getSkillsByCategory = (category: string) => {
  return skills.filter(s => s.category === category)
}
</script>

<template>
  <section id="skills" class="section skills">
    <div class="section-title">
      <span>Habilidades</span>
      <h2>Mi Stack <span class="gradient-text">Tecnológico</span></h2>
    </div>
    
    <div class="skills-container">
      <div 
        v-for="category in categories" 
        :key="category.id"
        class="skill-category"
      >
        <h3 class="category-title" :style="{ borderColor: category.color, color: category.color }">
          {{ category.label }}
        </h3>
        
        <div class="skills-grid">
          <div 
            v-for="(skill, index) in getSkillsByCategory(category.id)" 
            :key="skill.name"
            class="skill-card glass-card"
            :style="{ animationDelay: `${index * 0.05}s` }"
          >
            <div class="skill-icon-wrapper">
              <span class="skill-icon">{{ skill.icon }}</span>
            </div>
            <span class="skill-name">{{ skill.name }}</span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.skills {
  background: var(--color-bg-primary);
}

.skills-container {
  display: flex;
  flex-direction: column;
  gap: 4rem;
}

.category-title {
  font-size: 1.5rem;
  margin-bottom: 2rem;
  padding-left: 1rem;
  border-left: 4px solid;
  display: inline-block;
}

.skills-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(140px, 1fr));
  gap: 2rem;
}

.skill-card {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 1.5rem;
  gap: 1rem;
  text-align: center;
  transition: all 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275);
  border: 1px solid rgba(255, 255, 255, 0.05);
  background: rgba(255, 255, 255, 0.02);
}

.skill-card:hover {
  transform: translateY(-8px) scale(1.05);
  background: rgba(255, 255, 255, 0.05);
  border-color: rgba(255, 255, 255, 0.2);
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
}

.skill-icon-wrapper {
  width: 60px;
  height: 60px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 2.5rem;
  background: rgba(255, 255, 255, 0.03);
  border-radius: 50%;
  margin-bottom: 0.5rem;
  transition: background 0.3s ease;
}

.skill-card:hover .skill-icon-wrapper {
  background: rgba(255, 255, 255, 0.1);
}

.skill-name {
  font-weight: 600;
  font-size: 1rem;
  color: var(--text-primary);
}

@media (max-width: 640px) {
  .skills-grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 1rem;
  }
}
</style>
