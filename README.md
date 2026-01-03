<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Yaw Antwi's Portfolio</title>
    <!-- Font and Styling -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap" rel="stylesheet">
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">
    <style>
        body { font-family: 'Inter', sans-serif; overflow-x: hidden; }
        
        .hero-background {
            position: relative;
            background-image: url('https://i.imgur.com/geNH0KS.png');
            background-size: cover;
            background-position: center;
            background-repeat: no-repeat;
        }
        
        .hero-background::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: linear-gradient(to bottom, rgba(0, 0, 0, 0.7), #111827); 
            z-index: 10;
        }

        .hero-content { position: relative; z-index: 20; }

        .project-media-container {
            aspect-ratio: 16 / 9;
            background-color: #000;
            overflow: hidden;
        }

        .sql-code {
            font-family: 'Courier New', Courier, monospace;
            background: #1a1a1a;
            padding: 12px;
            border-radius: 8px;
            color: #14b8a6;
            font-size: 0.85rem;
            line-height: 1.5;
            border-left: 4px solid #14b8a6;
            margin-top: 10px;
        }

        /* Interactive Skill Card Styling */
        .skill-card {
            cursor: pointer;
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
            border: 1px solid #374151;
            background-color: #1f2937;
        }

        .skill-card:hover {
            transform: translateY(-10px);
            border-color: #14b8a6;
            background-color: #111827;
            box-shadow: 0 10px 30px -10px rgba(20, 184, 166, 0.3);
        }

        .skill-card img {
            filter: grayscale(100%) opacity(0.6);
            transition: all 0.4s ease;
        }

        .skill-card:hover img {
            filter: grayscale(0%) opacity(1);
            transform: scale(1.1);
        }

        /* Full Screen Project Overlay */
        #project-overlay {
            position: fixed;
            inset: 0;
            background-color: rgba(17, 24, 39, 0.98);
            z-index: 100;
            display: none;
            overflow-y: auto;
            backdrop-filter: blur(10px);
        }

        /* Animation for project entry */
        @keyframes slideUp {
            from { opacity: 0; transform: translateY(40px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .animate-pop {
            animation: slideUp 0.5s ease-out forwards;
        }

        .close-btn {
            position: fixed;
            top: 2rem;
            right: 2rem;
            z-index: 110;
            background: #374151;
            color: white;
            width: 50px;
            height: 50px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .close-btn:hover {
            background: #ef4444;
            transform: rotate(90deg);
        }

        /* Credentials and Education card styling */
        .credential-card {
            background: linear-gradient(145deg, #1f2937, #111827);
            border: 1px solid #374151;
            transition: all 0.3s ease;
        }
        .credential-card:hover {
            border-color: #14b8a6;
            transform: scale(1.02);
        }
    </style>
</head>
<body class="bg-gray-900 text-white selection:bg-teal-500/30">

    <!-- Hero Section -->
    <header class="min-h-screen flex flex-col justify-center items-center text-center hero-background px-6">
        <div class="hero-content max-w-4xl">
            <h1 class="text-5xl md:text-7xl font-bold mb-6 tracking-tight">Yaw Antwi</h1>
            <p class="text-xl md:text-2xl text-gray-300 mb-10 leading-relaxed text-balance">
                Data Analyst. Problem Solver. Visual Storyteller. I transform raw datasets into strategic assets through professional visualization and automated analytics.
            </p>
            <div class="flex flex-wrap justify-center gap-4">
                <a href="#skills-section" class="px-8 py-4 bg-teal-500 hover:bg-teal-600 text-white rounded-xl font-bold transition-all shadow-lg hover:-translate-y-1">
                    Explore My Portfolio
                </a>
            </div>
        </div>
    </header>

    <main class="container mx-auto px-6 py-20">
        
        <!-- Tool Navigation Section -->
        <section id="skills-section" class="py-20">
            <h2 class="text-4xl font-bold mb-4 text-center">Project Categories</h2>
            <p class="text-center text-gray-400 mb-16">Click a tool to view its specialized projects</p>
            
            <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-5 gap-6 max-w-7xl mx-auto">
                <!-- Excel Card -->
                <div class="skill-card p-10 rounded-3xl text-center" onclick="openProjects('excel')">
                    <img src="https://upload.wikimedia.org/wikipedia/commons/3/34/Microsoft_Excel_2013_logo.svg" alt="Excel" class="w-16 h-16 mx-auto mb-6">
                    <h4 class="text-xl font-bold">Excel</h4>
                    <p class="text-gray-500 text-sm mt-2">Dashboards & Formulas</p>
                </div>
                <!-- Power BI Card -->
                <div class="skill-card p-10 rounded-3xl text-center" onclick="openProjects('powerbi')">
                    <img src="https://upload.wikimedia.org/wikipedia/commons/c/cf/New_Power_BI_Logo.svg" alt="Power BI" class="w-16 h-16 mx-auto mb-6">
                    <h4 class="text-xl font-bold">Power BI</h4>
                    <p class="text-gray-500 text-sm mt-2">Interactive BI Reports</p>
                </div>
                <!-- SQL Card -->
                <div class="skill-card p-10 rounded-3xl text-center" onclick="openProjects('sql')">
                    <img src="https://cdn-icons-png.flaticon.com/512/2772/2772128.png" alt="SQL" class="w-16 h-16 mx-auto mb-6">
                    <h4 class="text-xl font-bold">SQL</h4>
                    <p class="text-gray-500 text-sm mt-2">Database Queries</p>
                </div>
                <!-- Tableau Card -->
                <div class="skill-card p-10 rounded-3xl text-center" onclick="openProjects('tableau')">
                    <img src="https://upload.wikimedia.org/wikipedia/commons/4/4b/Tableau_Logo.png" alt="Tableau" class="w-16 h-16 mx-auto mb-6">
                    <h4 class="text-xl font-bold">Tableau</h4>
                    <p class="text-gray-500 text-sm mt-2">Visual Storytelling</p>
                </div>
                <!-- Python Card -->
                <div class="skill-card p-10 rounded-3xl text-center" onclick="openProjects('python_colab')">
                    <img src="https://upload.wikimedia.org/wikipedia/commons/c/c3/Python-logo-notext.svg" alt="Python" class="w-16 h-16 mx-auto mb-6">
                    <h4 class="text-xl font-bold">Python</h4>
                    <p class="text-gray-500 text-sm mt-2">Data Science & ML</p>
                </div>
            </div>
        </section>

        <!-- Academic Foundation Section -->
        <section id="education" class="py-20">
            <div class="max-w-6xl mx-auto px-6">
                <h2 class="text-3xl font-bold mb-12 text-center">Academic Foundation</h2>
                <div class="grid md:grid-cols-2 gap-8">
                    <!-- Education Item 1 -->
                    <div class="credential-card p-8 rounded-3xl flex items-start gap-6">
                        <div class="bg-teal-500/10 p-4 rounded-2xl">
                            <i class="fas fa-graduation-cap text-3xl text-teal-400"></i>
                        </div>
                        <div>
                            <span class="text-teal-400 font-bold text-sm">2025</span>
                            <h3 class="text-xl font-bold mt-1">Post Baccalaureate Diploma in Business Analytics</h3>
                            <p class="text-gray-400 text-sm mt-2">Cape Breton University | Sydney, NS</p>
                        </div>
                    </div>
                    <!-- Education Item 2 -->
                    <div class="credential-card p-8 rounded-3xl flex items-start gap-6">
                        <div class="bg-teal-500/10 p-4 rounded-2xl">
                            <i class="fas fa-university text-3xl text-teal-400"></i>
                        </div>
                        <div>
                            <h3 class="text-xl font-bold mt-1">BSc in Banking and Finance</h3>
                            <p class="text-gray-400 text-sm mt-2">University of Professional Studies | Accra, Ghana</p>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Professional Credentials Section -->
        <section id="credentials" class="py-20 bg-gray-900/50 rounded-[3rem] mb-20">
            <div class="max-w-6xl mx-auto px-6">
                <h2 class="text-3xl font-bold mb-12 text-center">Professional Credentials</h2>
                <div class="grid md:grid-cols-2 gap-8">
                    <!-- IIBA Membership Card -->
                    <div class="credential-card p-8 rounded-3xl flex items-start gap-6">
                        <div class="bg-teal-500/10 p-4 rounded-2xl">
                            <i class="fas fa-id-badge text-3xl text-teal-400"></i>
                        </div>
                        <div>
                            <h3 class="text-xl font-bold mb-2">IIBA Professional Membership</h3>
                            <p class="text-gray-400 text-sm leading-relaxed mb-4 text-balance">
                                Active member of the International Institute of Business Analysis. Committed to best practices in business analysis and data-driven decision frameworks.
                            </p>
                            <span class="px-3 py-1 bg-teal-500/20 text-teal-400 text-xs font-bold rounded-full uppercase tracking-widest">Member In Good Standing</span>
                        </div>
                    </div>
                    <!-- Certifications Card -->
                    <div class="credential-card p-8 rounded-3xl flex items-start gap-6">
                        <div class="bg-teal-500/10 p-4 rounded-2xl">
                            <i class="fas fa-certificate text-3xl text-teal-400"></i>
                        </div>
                        <div>
                            <h3 class="text-xl font-bold mb-4">Professional Certifications</h3>
                            <ul class="text-gray-400 text-sm space-y-3">
                                <li class="flex items-center gap-2"><i class="fas fa-check-circle text-teal-500 text-xs"></i> SQL Fundamentals – Festman Learning Hub</li>
                                <li class="flex items-center gap-2"><i class="fas fa-check-circle text-teal-500 text-xs"></i> Data Visualization with Excel – Festman Learning Hub</li>
                                <li class="flex items-center gap-2"><i class="fas fa-check-circle text-teal-500 text-xs"></i> Power BI for Analytics – Festman Learning Hub</li>
                                <li class="flex items-center gap-2"><i class="fas fa-check-circle text-teal-500 text-xs"></i> Google Cybersecurity Professional Certificate</li>
                            </ul>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Project Overlay (The New Interface) -->
        <div id="project-overlay">
            <div class="close-btn" onclick="closeProjects()">
                <i class="fas fa-times fa-lg"></i>
            </div>
            
            <div class="container mx-auto px-6 py-24">
                <div class="text-center mb-16 animate-pop">
                    <h2 class="text-5xl font-bold mb-4" id="overlay-title">Excel Projects</h2>
                    <div class="h-1.5 w-32 bg-teal-500 mx-auto rounded-full shadow-[0_0_15px_rgba(20,184,166,0.5)]"></div>
                </div>

                <div id="overlay-grid" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-10">
                    <!-- Dynamic Projects Here -->
                </div>
            </div>
        </div>

        <!-- Contact Section -->
        <section id="contact" class="max-w-4xl mx-auto py-20 px-6">
            <div class="bg-gray-800 rounded-[3rem] p-12 border border-gray-700 shadow-2xl">
                <h2 class="text-3xl font-bold mb-10 text-center">Get In Touch</h2>
                <div class="grid md:grid-cols-2 gap-10">
                    <div class="space-y-6">
                        <p class="text-gray-400">Feel free to reach out for collaborations or project inquiries.</p>
                        <div class="flex items-center gap-4 text-teal-400">
                            <i class="fas fa-envelope"></i>
                            <a href="mailto:yawowusuantwi94@yahoo.com">yawowusuantwi94@yahoo.com</a>
                        </div>
                    </div>
                    <form class="space-y-4" onsubmit="event.preventDefault();">
                        <input type="text" placeholder="Your Name" class="w-full p-4 bg-gray-900 border border-gray-700 rounded-2xl focus:ring-2 focus:ring-teal-500 outline-none transition-all">
                        <textarea placeholder="Message" rows="4" class="w-full p-4 bg-gray-900 border border-gray-700 rounded-2xl focus:ring-2 focus:ring-teal-500 outline-none transition-all"></textarea>
                        <button class="w-full py-4 bg-teal-500 hover:bg-teal-600 font-bold rounded-2xl transition-all shadow-lg">Send Message</button>
                    </form>
                </div>
            </div>
        </section>
    </main>

    <footer class="py-12 text-center text-gray-500 border-t border-gray-800">
        <p>© 2024 Yaw Antwi | Portfolio Showcase</p>
    </footer>

    <script>
        const projects = [
            // EXCEL
            { title: "FestMan Hotel Booking Dashboard", desc: "Interactive overview of hotel bookings (2010–2021), focusing on customer demographics, booking fees, and net profit margins.", img: "https://i.imgur.com/0B4naR3.jpeg", tags: ["Excel", "Analytics"], filter: "excel" },
            { title: "Online Store Sales Dashboard", desc: "Analysis of e-commerce performance identifying revenue trends, order distribution, and high-value customer segments.", img: "https://i.imgur.com/7ytBq2W.jpeg", tags: ["Excel", "Sales"], filter: "excel" },
            { title: "Retail Superstore Dashboard", desc: "Comprehensive tracking of $0.5M in retail sales, regional growth patterns, and product category profitability.", img: "https://i.imgur.com/YoXn4RL.png", tags: ["Excel", "Retail"], filter: "excel" },
            { title: "Student Performance Dashboard", desc: "Correlating test scores with parental education and preparation factors to identify key academic drivers.", img: "https://i.imgur.com/3Mzt9xG.png", tags: ["Excel", "Education"], filter: "excel" },
            // POWER BI
            { title: "Walmart Sales Analysis", desc: "Visualizing the impact of economic factors (Unemployment, Fuel Prices) on weekly revenue trends across regions.", img: "https://i.imgur.com/vXg3LCX.png", tags: ["Power BI", "Economics"], filter: "powerbi" },
            { title: "Festman Hotel Booking Hub", desc: "High-level dashboard summarizing booking fees, profit trends, and global customer origin distribution.", img: "https://i.imgur.com/R3uzUzt.png", tags: ["Power BI", "BI"], filter: "powerbi" },
            { title: "Sales Performance Dashboard", desc: "Business-wide metrics tracking $8.34bn in revenue. Detailed views on brand contribution and regional channel performance.", img: "https://i.imgur.com/JqZ460s.png", tags: ["Power BI", "Finance"], filter: "powerbi" },
            // SQL
            { query: "SELECT FirstName, LastName, Country\nFROM Customer\nWHERE Country IN ('Brazil', 'Germany');", img: "https://i.imgur.com/fKYvh56.png", tags: ["SQL", "Extraction"], filter: "sql" },
            { query: "SELECT LastName, FirstName, BirthDate\nFROM Employee\nWHERE BirthDate = '1958-12-08 00:00:00';", img: "https://i.imgur.com/XnWZd60.png", tags: ["SQL", "Dates"], filter: "sql" },
            { query: "SELECT Name, Milliseconds, UnitPrice\nFROM Track\nWHERE Milliseconds BETWEEN 400000 AND 500000;", img: "https://i.imgur.com/TUNsiDC.png", tags: ["SQL", "Filtering"], filter: "sql" },
            // TABLEAU
            { title: "Fundamental Assessment Dashboard", desc: "Treemap and scatter plot analysis of industry revenue, comparing profitability and geographic spread of dominant firms.", img: "https://i.imgur.com/LjrMihR.png", tags: ["Tableau", "Treemap"], filter: "tableau" },
            // PYTHON
            { title: "LOAN RISK ASSESSMENT (ML)", desc: "Using K-Means and Logistic Regression to predict repayment likelihood and classify bank loan risk levels.", img: "https://i.imgur.com/0sfpQVs.jpeg", video: "https://i.imgur.com/xTIbjct.mp4", tags: ["Python", "ML"], filter: "python_colab" }
        ];

        function openProjects(category) {
            const overlay = document.getElementById('project-overlay');
            const grid = document.getElementById('overlay-grid');
            const title = document.getElementById('overlay-title');
            
            const names = {
                'excel': 'Excel Dashboards',
                'powerbi': 'Power BI Solutions',
                'sql': 'Advanced SQL Queries',
                'tableau': 'Tableau Analytics',
                'python_colab': 'Python & ML Models'
            };

            title.innerText = names[category];
            grid.innerHTML = '';
            
            const filtered = projects.filter(p => p.filter === category);
            
            filtered.forEach((p, index) => {
                const card = document.createElement('div');
                card.className = "bg-gray-800 rounded-3xl overflow-hidden border border-gray-700 shadow-2xl flex flex-col animate-pop";
                card.style.animationDelay = `${index * 0.1}s`;
                
                let mediaHtml = p.video ? 
                    `<div class="project-media-container relative"><img src="${p.img}" class="w-full h-full object-cover p-img"><video src="${p.video}" class="absolute inset-0 w-full h-full object-cover opacity-0 p-vid" loop muted playsinline></video></div>` :
                    `<div class="project-media-container"><img src="${p.img}" class="w-full h-full object-cover"></div>`;

                let contentHtml = category === 'sql' ? 
                    `<div class="p-8 flex-grow"><div class="sql-code">${p.query.replace(/\n/g, '<br>')}</div></div>` :
                    `<div class="p-8 flex-grow"><h3 class="text-xl font-bold mb-3">${p.title}</h3><p class="text-gray-400 text-sm leading-relaxed">${p.desc}</p></div>`;

                card.innerHTML = mediaHtml + contentHtml + `<div class="px-8 pb-8 flex gap-2">${p.tags.map(t => `<span class="px-3 py-1 bg-gray-900 text-[10px] uppercase font-bold tracking-widest text-teal-400 rounded-full border border-gray-700">${t}</span>`).join('')}</div>`;
                grid.appendChild(card);

                if (p.video) {
                    const img = card.querySelector('.p-img');
                    const vid = card.querySelector('.p-vid');
                    card.onmouseenter = () => { vid.play(); vid.style.opacity = 1; img.style.opacity = 0; };
                    card.onmouseleave = () => { vid.pause(); vid.style.opacity = 0; img.style.opacity = 1; };
                }
            });

            overlay.style.display = 'block';
            document.body.style.overflow = 'hidden'; 
        }

        function closeProjects() {
            document.getElementById('project-overlay').style.display = 'none';
            document.body.style.overflow = 'auto';
        }
    </script>
</body>
</html>
