import React, { useState } from 'react';
import { Copy, Download, Github, Code2, Database, Zap, Sparkles } from 'lucide-react';

export default function ProfileGenerator() {
  const [formData, setFormData] = useState({
    name: '',
    title: 'Backend Engineer',
    tagline: 'Crafting robust backend solutions with Laravel',
    location: '',
    company: '',
    github: '',
    linkedin: '',
    email: '',
    website: '', 
    
    // Skills
    primarySkills: ['Laravel', 'PHP', 'MySQL'],
    frameworks: ['Laravel', 'Lumen', 'Symfony'],
    databases: ['MySQL', 'PostgreSQL', 'Redis'],
    tools: ['Docker', 'Git', 'Postman'],
    erp: ['Odoo', 'ERPNext', 'Custom ERP'],
    
    // Stats
    yearsExp: '3',
    projectsCompleted: '50+',
    
    // Custom sections
    currentlyLearning: '',
    funFact: '',
    
    // Theme
    theme: 'professional'
  });

  const [copied, setCopied] = useState(false);
  const [activeTab, setActiveTab] = useState('form');

  const themes = {
    professional: {
      name: 'Professional Dark',
      emoji: '💼',
      headerBg: 'https://capsule-render.vercel.app/api?type=waving&color=0:667eea,100:764ba2&height=200&section=header&fontSize=40',
      badge: 'for-the-badge',
      color: '667eea'
    },
    modern: {
      name: 'Modern Gradient',
      emoji: '🎨',
      headerBg: 'https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=0,2,3,5,6&height=200&section=header&fontSize=40',
      badge: 'flat-square',
      color: '00d4ff'
    },
    minimal: {
      name: 'Clean Minimal',
      emoji: '✨',
      headerBg: 'https://capsule-render.vercel.app/api?type=slice&color=0:4facfe,100:00f2fe&height=180&section=header&fontSize=40',
      badge: 'flat',
      color: '4facfe'
    },
    vibrant: {
      name: 'Vibrant Energy',
      emoji: '⚡',
      headerBg: 'https://capsule-render.vercel.app/api?type=waving&color=0:ff6b6b,50:feca57,100:48dbfb&height=200&section=header&fontSize=40',
      badge: 'for-the-badge',
      color: 'ff6b6b'
    }
  };

  const skillCategories = {
    'Backend Frameworks': ['Laravel', 'Lumen', 'Symfony', 'CodeIgniter', 'Slim'],
    'Databases': ['MySQL', 'PostgreSQL', 'MongoDB', 'Redis', 'MariaDB', 'SQLite'],
    'ERP Systems': ['Odoo', 'ERPNext', 'Dolibarr', 'Custom ERP', 'SAP', 'Oracle ERP'],
    'DevOps & Tools': ['Docker', 'Git', 'Jenkins', 'GitLab CI', 'AWS', 'Linux'],
    'API & Testing': ['REST API', 'GraphQL', 'Postman', 'PHPUnit', 'Pest'],
    'Frontend (Basic)': ['Vue.js', 'Alpine.js', 'Livewire', 'Inertia.js', 'Blade']
  };

  const generateMarkdown = () => {
    const theme = themes[formData.theme];
    const name = formData.name || 'Your Name';
    const headerText = `text=${encodeURIComponent(name)}`;
    
    let markdown = `<div align="center">

<img src="${theme.headerBg}&${headerText}" />

# ${formData.tagline}

### ${formData.title}${formData.location ? ` • ${formData.location}` : ''}
${formData.company ? `**Currently at:** ${formData.company}` : ''}

`;

    // Contact badges
    if (formData.github || formData.linkedin || formData.email || formData.website) {
      markdown += `<p align="center">\n`;
      if (formData.github) {
        markdown += `  <a href="https://github.com/${formData.github}"><img src="https://img.shields.io/badge/GitHub-${formData.github}-181717?style=${theme.badge}&logo=github" /></a>\n`;
      }
      if (formData.linkedin) {
        markdown += `  <a href="https://linkedin.com/in/${formData.linkedin}"><img src="https://img.shields.io/badge/LinkedIn-Connect-0077B5?style=${theme.badge}&logo=linkedin" /></a>\n`;
      }
      if (formData.email) {
        markdown += `  <a href="mailto:${formData.email}"><img src="https://img.shields.io/badge/Email-Contact-D14836?style=${theme.badge}&logo=gmail&logoColor=white" /></a>\n`;
      }
      if (formData.website) {
        markdown += `  <a href="${formData.website}"><img src="https://img.shields.io/badge/Website-Visit-${theme.color}?style=${theme.badge}&logo=google-chrome&logoColor=white" /></a>\n`;
      }
      markdown += `</p>\n\n`;
    }

    markdown += `</div>

## 🚀 About Me

I'm a passionate **${formData.title}** specializing in building scalable backend solutions with **Laravel** and modern PHP frameworks. With **${formData.yearsExp}+ years** of experience, I've successfully delivered **${formData.projectsCompleted} projects** ranging from custom ERP systems to high-performance APIs.

${formData.currentlyLearning ? `🌱 Currently learning: **${formData.currentlyLearning}**\n` : ''}${formData.funFact ? `⚡ Fun fact: ${formData.funFact}\n` : ''}
---

## 🛠️ Tech Stack

### Backend Development
<p>
`;

    // Generate skill badges
    const allSkills = [...new Set([
      ...formData.frameworks,
      'PHP',
      ...formData.databases,
      ...formData.tools
    ])];

    const skillBadges = {
      'Laravel': 'FF2D20?logo=laravel&logoColor=white',
      'PHP': '777BB4?logo=php&logoColor=white',
      'MySQL': '4479A1?logo=mysql&logoColor=white',
      'PostgreSQL': '4169E1?logo=postgresql&logoColor=white',
      'MongoDB': '47A248?logo=mongodb&logoColor=white',
      'Redis': 'DC382D?logo=redis&logoColor=white',
      'Docker': '2496ED?logo=docker&logoColor=white',
      'Git': 'F05032?logo=git&logoColor=white',
      'Postman': 'FF6C37?logo=postman&logoColor=white',
      'Lumen': 'E74430?logo=lumen&logoColor=white',
      'Symfony': '000000?logo=symfony&logoColor=white',
      'CodeIgniter': 'EF4223?logo=codeigniter&logoColor=white',
      'MariaDB': '003545?logo=mariadb&logoColor=white',
      'SQLite': '003B57?logo=sqlite&logoColor=white',
      'AWS': '232F3E?logo=amazon-aws&logoColor=white',
      'Linux': 'FCC624?logo=linux&logoColor=black',
      'Jenkins': 'D24939?logo=jenkins&logoColor=white',
      'GitLab CI': 'FC6D26?logo=gitlab&logoColor=white',
      'Vue.js': '4FC08D?logo=vue.js&logoColor=white',
      'Alpine.js': '8BC0D0?logo=alpine.js&logoColor=white'
    };

    allSkills.forEach(skill => {
      const badge = skillBadges[skill] || `${theme.color}`;
      markdown += `  <img src="https://img.shields.io/badge/${skill.replace(/ /g, '%20')}-${badge}&style=${theme.badge}" />\n`;
    });

    markdown += `</p>

### ERP & Business Solutions
<p>
`;

    formData.erp.forEach(erp => {
      markdown += `  <img src="https://img.shields.io/badge/${erp.replace(/ /g, '%20')}-ERP%20System-${theme.color}?style=${theme.badge}" />\n`;
    });

    markdown += `</p>

---

## 📊 GitHub Stats

<div align="center">
  <img height="180em" src="https://github-readme-stats.vercel.app/api?username=${formData.github || 'username'}&show_icons=true&theme=radical&include_all_commits=true&count_private=true"/>
  <img height="180em" src="https://github-readme-stats.vercel.app/api/top-langs/?username=${formData.github || 'username'}&layout=compact&langs_count=8&theme=radical"/>
</div>

<div align="center">
  <img src="https://github-readme-streak-stats.herokuapp.com/?user=${formData.github || 'username'}&theme=radical" />
</div>

---

## 🏆 Achievements

<div align="center">
  <img src="https://github-profile-trophy.vercel.app/?username=${formData.github || 'username'}&theme=radical&no-frame=true&no-bg=false&margin-w=4&row=1" />
</div>

---

## 💼 What I Do

- 🏗️ **Backend Architecture**: Design and implement scalable Laravel applications
- 🔌 **API Development**: Build robust RESTful APIs with Laravel Sanctum/Passport
- 📦 **ERP Solutions**: Develop custom ERP modules and integrate existing systems
- 🗄️ **Database Design**: Optimize database schemas and queries for performance
- 🐳 **DevOps**: Deploy and maintain applications using Docker and CI/CD pipelines
- 🔒 **Security**: Implement authentication, authorization, and security best practices

---

## 📫 Let's Connect!

I'm always open to interesting conversations and collaboration opportunities. Feel free to reach out!

<div align="center">
  
${formData.email ? `📧 **Email**: ${formData.email}  \n` : ''}${formData.github ? `💼 **GitHub**: [@${formData.github}](https://github.com/${formData.github})  \n` : ''}${formData.linkedin ? `🔗 **LinkedIn**: [${formData.linkedin}](https://linkedin.com/in/${formData.linkedin})  \n` : ''}
<img src="https://capsule-render.vercel.app/api?type=waving&color=${theme.headerBg.includes('gradient') ? 'gradient' : '0:667eea,100:764ba2'}&height=120&section=footer" />

</div>`;

    return markdown;
  };

  const copyToClipboard = () => {
    navigator.clipboard.writeText(generateMarkdown());
    setCopied(true);
    setTimeout(() => setCopied(false), 2000);
  };

  const downloadMarkdown = () => {
    const blob = new Blob([generateMarkdown()], { type: 'text/markdown' });
    const url = URL.createObjectURL(blob);
    const a = document.createElement('a');
    a.href = url;
    a.download = 'README.md';
    a.click();
  };

  const toggleSkill = (category, skill) => {
    const categoryMap = {
      'Backend Frameworks': 'frameworks',
      'Databases': 'databases',
      'DevOps & Tools': 'tools',
      'ERP Systems': 'erp'
    };
    
    const field = categoryMap[category];
    if (!field) return;
    
    setFormData(prev => {
      const current = prev[field];
      const updated = current.includes(skill)
        ? current.filter(s => s !== skill)
        : [...current, skill];
      return { ...prev, [field]: updated };
    });
  };

  return (
    <div className="min-h-screen bg-gradient-to-br from-slate-900 via-purple-900 to-slate-900 text-white p-6">
      <div className="max-w-7xl mx-auto">
        {/* Header */}
        <div className="text-center mb-8">
          <div className="flex items-center justify-center gap-3 mb-4">
            <Github className="w-12 h-12 text-purple-400" />
            <h1 className="text-4xl font-bold bg-gradient-to-r from-purple-400 to-pink-400 bg-clip-text text-transparent">
              Laravel Profile README Generator
            </h1>
          </div>
          <p className="text-slate-300 text-lg">
            Buat profile GitHub yang profesional dan menarik untuk Backend Engineer
          </p>
        </div>

        {/* Tabs */}
        <div className="flex gap-2 mb-6 bg-slate-800/50 p-1 rounded-lg backdrop-blur">
          <button
            onClick={() => setActiveTab('form')}
            className={`flex-1 py-3 px-6 rounded-lg font-semibold transition-all ${
              activeTab === 'form'
                ? 'bg-purple-600 text-white shadow-lg shadow-purple-500/50'
                : 'text-slate-400 hover:text-white'
            }`}
          >
            <Code2 className="w-5 h-5 inline mr-2" />
            Form Input
          </button>
          <button
            onClick={() => setActiveTab('preview')}
            className={`flex-1 py-3 px-6 rounded-lg font-semibold transition-all ${
              activeTab === 'preview'
                ? 'bg-purple-600 text-white shadow-lg shadow-purple-500/50'
                : 'text-slate-400 hover:text-white'
            }`}
          >
            <Sparkles className="w-5 h-5 inline mr-2" />
            Preview & Export
          </button>
        </div>

        <div className="grid grid-cols-1 gap-6">
          {/* Form Section */}
          {activeTab === 'form' && (
            <div className="bg-slate-800/50 backdrop-blur rounded-xl p-6 shadow-2xl border border-slate-700">
              <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
                {/* Basic Info */}
                <div className="space-y-4">
                  <h3 className="text-xl font-bold text-purple-400 flex items-center gap-2">
                    <Database className="w-5 h-5" />
                    Informasi Dasar
                  </h3>
                  
                  <div>
                    <label className="block text-sm font-medium mb-2">Nama Lengkap</label>
                    <input
                      type="text"
                      value={formData.name}
                      onChange={(e) => setFormData({...formData, name: e.target.value})}
                      className="w-full bg-slate-900 border border-slate-600 rounded-lg px-4 py-2 focus:ring-2 focus:ring-purple-500 focus:border-transparent"
                      placeholder="John Doe"
                    />
                  </div>

                  <div>
                    <label className="block text-sm font-medium mb-2">Job Title</label>
                    <input
                      type="text"
                      value={formData.title}
                      onChange={(e) => setFormData({...formData, title: e.target.value})}
                      className="w-full bg-slate-900 border border-slate-600 rounded-lg px-4 py-2 focus:ring-2 focus:ring-purple-500 focus:border-transparent"
                      placeholder="Backend Engineer"
                    />
                  </div>

                  <div>
                    <label className="block text-sm font-medium mb-2">Tagline</label>
                    <input
                      type="text"
                      value={formData.tagline}
                      onChange={(e) => setFormData({...formData, tagline: e.target.value})}
                      className="w-full bg-slate-900 border border-slate-600 rounded-lg px-4 py-2 focus:ring-2 focus:ring-purple-500 focus:border-transparent"
                      placeholder="Crafting robust backend solutions"
                    />
                  </div>

                  <div className="grid grid-cols-2 gap-4">
                    <div>
                      <label className="block text-sm font-medium mb-2">Lokasi</label>
                      <input
                        type="text"
                        value={formData.location}
                        onChange={(e) => setFormData({...formData, location: e.target.value})}
                        className="w-full bg-slate-900 border border-slate-600 rounded-lg px-4 py-2 focus:ring-2 focus:ring-purple-500 focus:border-transparent"
                        placeholder="Jakarta, ID"
                      />
                    </div>
                    <div>
                      <label className="block text-sm font-medium mb-2">Perusahaan</label>
                      <input
                        type="text"
                        value={formData.company}
                        onChange={(e) => setFormData({...formData, company: e.target.value})}
                        className="w-full bg-slate-900 border border-slate-600 rounded-lg px-4 py-2 focus:ring-2 focus:ring-purple-500 focus:border-transparent"
                        placeholder="Tech Corp"
                      />
                    </div>
                  </div>

                  <div className="grid grid-cols-2 gap-4">
                    <div>
                      <label className="block text-sm font-medium mb-2">Pengalaman (tahun)</label>
                      <input
                        type="text"
                        value={formData.yearsExp}
                        onChange={(e) => setFormData({...formData, yearsExp: e.target.value})}
                        className="w-full bg-slate-900 border border-slate-600 rounded-lg px-4 py-2 focus:ring-2 focus:ring-purple-500 focus:border-transparent"
                        placeholder="3"
                      />
                    </div>
                    <div>
                      <label className="block text-sm font-medium mb-2">Proyek Selesai</label>
                      <input
                        type="text"
                        value={formData.projectsCompleted}
                        onChange={(e) => setFormData({...formData, projectsCompleted: e.target.value})}
                        className="w-full bg-slate-900 border border-slate-600 rounded-lg px-4 py-2 focus:ring-2 focus:ring-purple-500 focus:border-transparent"
                        placeholder="50+"
                      />
                    </div>
                  </div>
                </div>

                {/* Contact Info */}
                <div className="space-y-4">
                  <h3 className="text-xl font-bold text-purple-400 flex items-center gap-2">
                    <Zap className="w-5 h-5" />
                    Kontak & Sosial Media
                  </h3>

                  <div>
                    <label className="block text-sm font-medium mb-2">GitHub Username</label>
                    <input
                      type="text"
                      value={formData.github}
                      onChange={(e) => setFormData({...formData, github: e.target.value})}
                      className="w-full bg-slate-900 border border-slate-600 rounded-lg px-4 py-2 focus:ring-2 focus:ring-purple-500 focus:border-transparent"
                      placeholder="johndoe"
                    />
                  </div>

                  <div>
                    <label className="block text-sm font-medium mb-2">LinkedIn Username</label>
                    <input
                      type="text"
                      value={formData.linkedin}
                      onChange={(e) => setFormData({...formData, linkedin: e.target.value})}
                      className="w-full bg-slate-900 border border-slate-600 rounded-lg px-4 py-2 focus:ring-2 focus:ring-purple-500 focus:border-transparent"
                      placeholder="johndoe"
                    />
                  </div>

                  <div>
                    <label className="block text-sm font-medium mb-2">Email</label>
                    <input
                      type="email"
                      value={formData.email}
                      onChange={(e) => setFormData({...formData, email: e.target.value})}
                      className="w-full bg-slate-900 border border-slate-600 rounded-lg px-4 py-2 focus:ring-2 focus:ring-purple-500 focus:border-transparent"
                      placeholder="john@example.com"
                    />
                  </div>

                  <div>
                    <label className="block text-sm font-medium mb-2">Website</label>
                    <input
                      type="url"
                      value={formData.website}
                      onChange={(e) => setFormData({...formData, website: e.target.value})}
                      className="w-full bg-slate-900 border border-slate-600 rounded-lg px-4 py-2 focus:ring-2 focus:ring-purple-500 focus:border-transparent"
                      placeholder="https://johndoe.com"
                    />
                  </div>

                  <div>
                    <label className="block text-sm font-medium mb-2">Sedang Belajar</label>
                    <input
                      type="text"
                      value={formData.currentlyLearning}
                      onChange={(e) => setFormData({...formData, currentlyLearning: e.target.value})}
                      className="w-full bg-slate-900 border border-slate-600 rounded-lg px-4 py-2 focus:ring-2 focus:ring-purple-500 focus:border-transparent"
                      placeholder="Microservices Architecture"
                    />
                  </div>

                  <div>
                    <label className="block text-sm font-medium mb-2">Fun Fact</label>
                    <input
                      type="text"
                      value={formData.funFact}
                      onChange={(e) => setFormData({...formData, funFact: e.target.value})}
                      className="w-full bg-slate-900 border border-slate-600 rounded-lg px-4 py-2 focus:ring-2 focus:ring-purple-500 focus:border-transparent"
                      placeholder="I debug with console.log 😄"
                    />
                  </div>
                </div>
              </div>

              {/* Skills Selection */}
              <div className="mt-8">
                <h3 className="text-xl font-bold text-purple-400 mb-4">Pilih Skills & Tools</h3>
                <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
                  {Object.entries(skillCategories).map(([category, skills]) => (
                    <div key={category} className="bg-slate-900/50 p-4 rounded-lg">
                      <h4 className="font-semibold text-purple-300 mb-3">{category}</h4>
                      <div className="flex flex-wrap gap-2">
                        {skills.map(skill => {
                          const categoryMap = {
                            'Backend Frameworks': 'frameworks',
                            'Databases': 'databases',
                            'DevOps & Tools': 'tools',
                            'ERP Systems': 'erp'
                          };
                          const field = categoryMap[category];
                          const isSelected = field && formData[field]?.includes(skill);
                          
                          return (
                            <button
                              key={skill}
                              onClick={() => toggleSkill(category, skill)}
                              className={`px-3 py-1 rounded-full text-sm font-medium transition-all ${
                                isSelected
                                  ? 'bg-purple-600 text-white shadow-lg shadow-purple-500/50'
                                  : 'bg-slate-700 text-slate-300 hover:bg-slate-600'
                              }`}
                            >
                              {skill}
                            </button>
                          );
                        })}
                      </div>
                    </div>
                  ))}
                </div>
              </div>

              {/* Theme Selection */}
              <div className="mt-8">
                <h3 className="text-xl font-bold text-purple-400 mb-4">Pilih Theme</h3>
                <div className="grid grid-cols-2 md:grid-cols-4 gap-4">
                  {Object.entries(themes).map(([key, theme]) => (
                    <button
                      key={key}
                      onClick={() => setFormData({...formData, theme: key})}
                      className={`p-4 rounded-lg border-2 transition-all ${
                        formData.theme === key
                          ? 'border-purple-500 bg-purple-900/30 shadow-lg shadow-purple-500/30'
                          : 'border-slate-600 bg-slate-900/50 hover:border-slate-500'
                      }`}
                    >
                      <div className="text-3xl mb-2">{theme.emoji}</div>
                      <div className="font-semibold text-sm">{theme.name}</div>
                    </button>
                  ))}
                </div>
              </div>
            </div>
          )}

          {/* Preview Section */}
          {activeTab === 'preview' && (
            <div className="space-y-6">
              <div className="bg-slate-800/50 backdrop-blur rounded-xl p-6 shadow-2xl border border-slate-700">
                <div className="flex items-center justify-between mb-4">
                  <h3 className="text-xl font-bold text-purple-400">Markdown Preview</h3>
                  <div className="flex gap-3">
                    <button
                      onClick={copyToClipboard}
                      className="flex items-center gap-2 bg-purple-600 hover:bg-purple-700 px-4 py-2 rounded-lg font-semibold transition-all shadow-lg shadow-purple-500/50"
                    >
                      <Copy className="w-4 h-4" />
                      {copied ? 'Copied!' : 'Copy'}
                    </button>
                    <button
                      onClick={downloadMarkdown}
                      className="flex items-center gap-2 bg-pink-600 hover:bg-pink-700 px-4 py-2 rounded-lg font-semibold transition-all shadow-lg shadow-pink-500/50"
                    >
                      <Download className="w-4 h-4" />
                      Download
                    </button>
                  </div>
                </div>
                <div className="bg-slate-900 rounded-lg p-4 overflow-x-auto">
                  <pre className="text-sm text-slate-300 whitespace-pre-wrap font-mono">
                    {generateMarkdown()}
                  </pre>
                </div>
              </div>

              {/* Instructions */}
              <div className="bg-gradient-to-r from-purple-900/50 to-pink-900/50 backdrop-blur rounded-xl p-6 border border-purple-500/30">
                <h3 className="text-xl font-bold text-purple-300 mb-4">📋 Cara Menggunakan</h3>
                <ol className="space-y-2 text-slate-300">
                  <li>1. Klik tombol <strong className="text-purple-300">Copy</strong> atau <strong className="text-purple-300">Download</strong> di atas</li>
                  <li>2. Buka repository GitHub Anda</li>
                  <li>3. Buat atau edit file <code className="bg-slate-800 px-2 py-1 rounded text-purple-300">README.md</code></li>
                  <li>4. Paste konten yang sudah di-copy</li>
                  <li>5. Commit dan push perubahan Anda</li>
                  <li>6. Profile README Anda siap! 🎉</li>
                </ol>
              </div>
            </div>
          )}
        </div>
      </div>
    </div>
  );
}
