# Intelligent-AI-Digest-for-Security
Intelligent AI Digest for Security, Privacy, and Compliance Feeds
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Intelligent AI Security Digest | n8n Workflow Guide</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Chart.js -->
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        cyber: {
                            bg: '#0f172a',    // Slate 900
                            card: '#1e293b',  // Slate 800
                            text: '#f8fafc',  // Slate 50
                            primary: '#06b6d4', // Cyan 500
                            ai: '#8b5cf6',    // Violet 500
                            alert: '#ef4444', // Red 500
                            safe: '#10b981',  // Emerald 500
                            muted: '#94a3b8'  // Slate 400
                        }
                    },
                    fontFamily: {
                        sans: ['Inter', 'system-ui', 'sans-serif'],
                        mono: ['Fira Code', 'monospace']
                    }
                }
            }
        }
    </script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;800&family=Fira+Code&display=swap');
        
        body {
            background-color: #0f172a;
            color: #f8fafc;
            font-family: 'Inter', sans-serif;
        }

        /* Chart Container Standards */
        .chart-container {
            position: relative;
            width: 100%;
            max-width: 600px; /* Constraint for large screens */
            height: 350px;
            max-height: 400px;
            margin-left: auto;
            margin-right: auto;
        }

        /* Responsive height adjustments */
        @media (max-width: 768px) {
            .chart-container {
                height: 300px;
            }
        }

        /* Utilities for "No SVG" Graphics */
        .cyber-grid {
            background-image: linear-gradient(rgba(6, 182, 212, 0.05) 1px, transparent 1px),
            linear-gradient(90deg, rgba(6, 182, 212, 0.05) 1px, transparent 1px);
            background-size: 20px 20px;
        }

        .glass-panel {
            background: rgba(30, 41, 59, 0.7);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(148, 163, 184, 0.1);
        }
    </style>
    <!-- 
        NARRATIVE PLAN:
        1. Title/Intro: The concept of the AI Analyst.
        2. The Challenge: Information Overload stats.
        3. The Workflow: Block diagram of the n8n process.
        4. Data Sources: Donut chart of the RSS feeds.
        5. AI Logic: Bar chart of severity scoring.
        6. Roadmap: Vertical timeline of implementation phases.
        
        PALETTE: Cyber Watch (Dark Navy, Electric Cyan, Neon Violet)
        NO SVG USED. NO MERMAID JS USED.
    -->
</head>
<body class="cyber-grid min-h-screen">

    <!-- Header Section -->
    <header class="w-full py-12 px-4 md:px-8 border-b border-cyber-card bg-cyber-bg/90 sticky top-0 z-50 backdrop-blur-md">
        <div class="max-w-7xl mx-auto flex flex-col md:flex-row items-center justify-between gap-4">
            <div>
                <h1 class="text-3xl md:text-5xl font-extrabold tracking-tight text-cyber-text">
                    <span class="text-cyber-primary">Intelligent</span> AI Security Digest
                </h1>
                <p class="mt-2 text-cyber-muted text-lg">
                    Build an automated <span class="text-cyber-ai font-semibold">AI Analyst</span> with n8n to monitor, filter, and summarize global threats.
                </p>
            </div>
            <div class="flex items-center space-x-4">
                <div class="px-4 py-2 rounded-full bg-cyber-card border border-cyber-primary/30 text-cyber-primary font-mono text-sm">
                    n8n Workflow
                </div>
                <div class="px-4 py-2 rounded-full bg-cyber-card border border-cyber-ai/30 text-cyber-ai font-mono text-sm">
                    AI Agent
                </div>
            </div>
        </div>
    </header>

    <main class="max-w-7xl mx-auto px-4 md:px-8 py-12 space-y-24">

        <!-- SECTION 1: THE PROBLEM (KPIs) -->
        <section class="grid grid-cols-1 md:grid-cols-3 gap-8">
            <div class="col-span-1 md:col-span-3 mb-4">
                <h2 class="text-2xl font-bold text-cyber-primary mb-4 border-l-4 border-cyber-primary pl-4">The Challenge: Signal vs. Noise</h2>
                <p class="text-cyber-muted max-w-3xl">
                    Security teams are overwhelmed. Thousands of RSS updates are published daily from CISA, NIST, and compliance bodies. 
                    Manually filtering this data leads to fatigue and missed critical alerts. We need automation to separate the signal from the noise.
                </p>
            </div>

            <!-- Stat Card 1 -->
            <div class="glass-panel rounded-xl p-8 text-center hover:border-cyber-primary/50 transition-colors duration-300">
                <div class="text-6xl mb-4">📢</div>
                <h3 class="text-4xl font-bold text-cyber-text mb-2">1000+</h3>
                <p class="text-cyber-primary font-medium uppercase tracking-wider text-sm">Daily Articles</p>
                <p class="mt-4 text-sm text-cyber-muted">Raw volume across security, privacy, and compliance feeds.</p>
            </div>

            <!-- Stat Card 2 -->
            <div class="glass-panel rounded-xl p-8 text-center hover:border-cyber-alert/50 transition-colors duration-300">
                <div class="text-6xl mb-4">⏳</div>
                <h3 class="text-4xl font-bold text-cyber-text mb-2">4 Hrs</h3>
                <p class="text-cyber-alert font-medium uppercase tracking-wider text-sm">Manual Effort</p>
                <p class="mt-4 text-sm text-cyber-muted">Time wasted daily reading irrelevant updates and duplicates.</p>
            </div>

            <!-- Stat Card 3 -->
            <div class="glass-panel rounded-xl p-8 text-center hover:border-cyber-safe/50 transition-colors duration-300">
                <div class="text-6xl mb-4">🤖</div>
                <h3 class="text-4xl font-bold text-cyber-text mb-2">1 Digest</h3>
                <p class="text-cyber-safe font-medium uppercase tracking-wider text-sm">Optimized Output</p>
                <p class="mt-4 text-sm text-cyber-muted">Consolidated, ranked, and summarized report delivered at 8 AM.</p>
            </div>
        </section>

        <!-- SECTION 2: THE WORKFLOW (Structured Diagram) -->
        <section>
            <h2 class="text-2xl font-bold text-cyber-primary mb-6 border-l-4 border-cyber-primary pl-4">The Automation Architecture</h2>
            <p class="text-cyber-muted mb-12 max-w-3xl">
                The n8n workflow follows a logical 5-phase pipeline. It begins with raw ingestion, filters based on recency, 
                analyzes content using an LLM (Large Language Model), groups the findings, and delivers a polished report.
            </p>

            <div class="relative w-full overflow-x-auto pb-8">
                <div class="min-w-[800px] grid grid-cols-5 gap-4 items-stretch">
                    
                    <!-- Node 1 -->
                    <div class="flex flex-col h-full">
                        <div class="bg-cyber-card border-t-4 border-cyber-muted rounded-b-lg p-6 flex-1 shadow-lg relative group">
                            <div class="absolute -top-3 left-1/2 transform -translate-x-1/2 bg-cyber-bg px-2 text-2xl">📡</div>
                            <h4 class="font-bold text-center mt-4 mb-2 text-cyber-text">1. Ingest</h4>
                            <p class="text-xs text-cyber-muted text-center leading-relaxed">
                                Schedule Trigger (8 AM)<br>+<br>RSS Feed Read Node
                            </p>
                        </div>
                        <div class="h-12 flex items-center justify-center text-cyber-muted text-2xl font-bold opacity-50">⬇</div>
                    </div>

                    <!-- Node 2 -->
                    <div class="flex flex-col h-full">
                        <div class="bg-cyber-card border-t-4 border-cyber-primary rounded-b-lg p-6 flex-1 shadow-lg relative">
                            <div class="absolute -top-3 left-1/2 transform -translate-x-1/2 bg-cyber-bg px-2 text-2xl">🛁</div>
                            <h4 class="font-bold text-center mt-4 mb-2 text-cyber-text">2. Filter</h4>
                            <p class="text-xs text-cyber-muted text-center leading-relaxed">
                                Filter by Date (> 24h)<br>+<br>Deduplication
                            </p>
                        </div>
                        <div class="h-12 flex items-center justify-center text-cyber-muted text-2xl font-bold opacity-50">⬇</div>
                    </div>

                    <!-- Node 3 -->
                    <div class="flex flex-col h-full">
                        <div class="bg-cyber-card border-t-4 border-cyber-ai rounded-b-lg p-6 flex-1 shadow-lg relative">
                            <div class="absolute -top-3 left-1/2 transform -translate-x-1/2 bg-cyber-bg px-2 text-2xl">🧠</div>
                            <h4 class="font-bold text-center mt-4 mb-2 text-cyber-ai">3. Analyze</h4>
                            <p class="text-xs text-cyber-muted text-center leading-relaxed">
                                AI Agent (LLM)<br>Summarize & Score<br>Parse JSON
                            </p>
                        </div>
                        <div class="h-12 flex items-center justify-center text-cyber-muted text-2xl font-bold opacity-50">⬇</div>
                    </div>

                    <!-- Node 4 -->
                    <div class="flex flex-col h-full">
                        <div class="bg-cyber-card border-t-4 border-cyber-safe rounded-b-lg p-6 flex-1 shadow-lg relative">
                            <div class="absolute -top-3 left-1/2 transform -translate-x-1/2 bg-cyber-bg px-2 text-2xl">📊</div>
                            <h4 class="font-bold text-center mt-4 mb-2 text-cyber-text">4. Aggregate</h4>
                            <p class="text-xs text-cyber-muted text-center leading-relaxed">
                                Group by Severity<br>Build HTML Report<br>Rank Content
                            </p>
                        </div>
                        <div class="h-12 flex items-center justify-center text-cyber-muted text-2xl font-bold opacity-50">⬇</div>
                    </div>

                    <!-- Node 5 -->
                    <div class="flex flex-col h-full">
                        <div class="bg-cyber-card border-t-4 border-cyber-text rounded-b-lg p-6 flex-1 shadow-lg relative">
                            <div class="absolute -top-3 left-1/2 transform -translate-x-1/2 bg-cyber-bg px-2 text-2xl">📧</div>
                            <h4 class="font-bold text-center mt-4 mb-2 text-cyber-text">5. Deliver</h4>
                            <p class="text-xs text-cyber-muted text-center leading-relaxed">
                                Gmail (HTML Body)<br>OR<br>Slack (Block Kit)
                            </p>
                        </div>
                    </div>

                </div>
                
                <!-- Connector Line visual helper -->
                <div class="absolute top-[50%] left-0 w-full h-1 bg-gradient-to-r from-cyber-card via-cyber-ai to-cyber-card -z-10 opacity-20 hidden md:block"></div>
            </div>
        </section>

        <!-- SECTION 3: DATA SOURCES (Donut Chart) -->
        <section class="grid grid-cols-1 md:grid-cols-2 gap-12 items-center">
            <div>
                <h2 class="text-2xl font-bold text-cyber-primary mb-6 border-l-4 border-cyber-primary pl-4">Intelligence Sources</h2>
                <p class="text-cyber-muted mb-6">
                    A robust digest relies on diverse, high-authority sources. The workflow ingests from three primary pillars: 
                    <strong>Security</strong> (Vulnerabilities), <strong>Privacy</strong> (Legal/Rights), and <strong>Compliance</strong> (Regulations).
                    Using multiple sources ensures comprehensive coverage of the threat landscape.
                </p>
                <ul class="space-y-3 mb-8">
                    <li class="flex items-center text-sm text-cyber-text">
                        <span class="w-3 h-3 rounded-full bg-cyber-alert mr-3"></span>
                        <span class="font-mono text-cyber-primary w-24">Security</span>
                        <span class="text-cyber-muted">CISA, The Hacker News, Bleeping Computer</span>
                    </li>
                    <li class="flex items-center text-sm text-cyber-text">
                        <span class="w-3 h-3 rounded-full bg-cyber-ai mr-3"></span>
                        <span class="font-mono text-cyber-primary w-24">Privacy</span>
                        <span class="text-cyber-muted">IAPP News</span>
                    </li>
                    <li class="flex items-center text-sm text-cyber-text">
                        <span class="w-3 h-3 rounded-full bg-cyber-safe mr-3"></span>
                        <span class="font-mono text-cyber-primary w-24">Compliance</span>
                        <span class="text-cyber-muted">GDPR Info, NIST News</span>
                    </li>
                </ul>
            </div>
            
            <div class="glass-panel p-6 rounded-xl">
                <div class="chart-container">
                    <canvas id="sourceChart"></canvas>
                </div>
                <p class="text-center text-xs text-cyber-muted mt-4">Distribution of Monitored RSS Feeds by Category</p>
            </div>
        </section>

        <!-- SECTION 4: AI ANALYSIS (Bar Chart) -->
        <section class="grid grid-cols-1 md:grid-cols-2 gap-12 items-center">
            <!-- Order swap on mobile -->
            <div class="glass-panel p-6 rounded-xl order-2 md:order-1">
                <div class="chart-container">
                    <canvas id="severityChart"></canvas>
                </div>
                <p class="text-center text-xs text-cyber-muted mt-4">Simulated Daily Threat Severity Classification</p>
            </div>

            <div class="order-1 md:order-2">
                <h2 class="text-2xl font-bold text-cyber-ai mb-6 border-l-4 border-cyber-ai pl-4">Inside the AI Brain</h2>
                <p class="text-cyber-muted mb-6">
                    The core value of this workflow is the AI Agent. It doesn't just read; it <strong>understands</strong>. 
                    Using a structured system prompt, the LLM analyzes each article to assign a <span class="text-white font-bold">Severity Score</span>.
                </p>
                <div class="bg-cyber-card rounded-lg p-4 border border-cyber-muted/20 font-mono text-xs text-cyber-muted mb-6">
                    <p class="text-cyber-ai mb-2">// System Prompt Logic</p>
                    <p>Analyze title & content. Return JSON:</p>
                    <ul class="ml-4 list-disc space-y-1 mt-2">
                        <li><span class="text-cyber-primary">summary</span>: 2-sentence overview</li>
                        <li><span class="text-cyber-primary">category</span>: [Security, Privacy, Compliance]</li>
                        <li><span class="text-cyber-primary">severity</span>: [Critical, High, Medium, Low]</li>
                        <li><span class="text-cyber-primary">action_required</span>: Boolean (true/false)</li>
                    </ul>
                </div>
                <p class="text-cyber-muted text-sm">
                    This allows the final report to highlight <strong>Critical</strong> threats (Red) while summarizing <strong>Low</strong> severity news (Blue) at the bottom, ensuring immediate attention where it matters most.
                </p>
            </div>
        </section>

        <!-- SECTION 5: IMPLEMENTATION ROADMAP (Timeline) -->
        <section>
            <h2 class="text-2xl font-bold text-cyber-safe mb-10 border-l-4 border-cyber-safe pl-4">Implementation Roadmap</h2>
            <p class="text-cyber-muted mb-12 max-w-3xl">
                Building this automation in n8n is straightforward. Follow these five phases to go from zero to a fully functional AI security analyst.
            </p>

            <div class="relative pl-8 md:pl-0">
                <!-- Vertical Line -->
                <div class="absolute left-8 md:left-1/2 top-0 bottom-0 w-1 bg-cyber-card transform md:-translate-x-1/2"></div>

                <!-- Phase 1 -->
                <div class="relative z-10 mb-16 md:flex md:justify-between items-center group">
                    <div class="md:w-[45%] mb-4 md:mb-0 md:text-right">
                        <h3 class="text-xl font-bold text-cyber-text">Phase 1: Trigger & Ingest</h3>
                        <p class="text-cyber-muted mt-2 text-sm">Set up the 8:00 AM Schedule Trigger and define your RSS feed URLs in a Code node array for cleaner management.</p>
                    </div>
                    <div class="absolute left-8 md:left-1/2 w-8 h-8 bg-cyber-bg border-4 border-cyber-primary rounded-full transform -translate-x-[1.2rem] md:-translate-x-1/2 flex items-center justify-center">
                        <span class="text-xs font-bold text-cyber-primary">1</span>
                    </div>
                    <div class="md:w-[45%] pl-8 md:pl-0">
                        <span class="inline-block px-3 py-1 bg-cyber-card border border-cyber-primary text-cyber-primary text-xs rounded">n8n: Schedule Node</span>
                    </div>
                </div>

                <!-- Phase 2 -->
                <div class="relative z-10 mb-16 md:flex md:justify-between items-center group">
                    <div class="md:w-[45%] order-2 md:order-1 pl-8 md:pl-0 md:text-right">
                         <span class="inline-block px-3 py-1 bg-cyber-card border border-cyber-primary text-cyber-primary text-xs rounded">n8n: Filter Node</span>
                    </div>
                    <div class="absolute left-8 md:left-1/2 w-8 h-8 bg-cyber-bg border-4 border-cyber-primary rounded-full transform -translate-x-[1.2rem] md:-translate-x-1/2 flex items-center justify-center">
                        <span class="text-xs font-bold text-cyber-primary">2</span>
                    </div>
                    <div class="md:w-[45%] order-1 md:order-2 mb-4 md:mb-0">
                        <h3 class="text-xl font-bold text-cyber-text">Phase 2: Cleaning</h3>
                        <p class="text-cyber-muted mt-2 text-sm">Filter out articles older than 24 hours using <code>$now.minus({hours: 24})</code> to ensure relevance and reduce token costs.</p>
                    </div>
                </div>

                <!-- Phase 3 -->
                <div class="relative z-10 mb-16 md:flex md:justify-between items-center group">
                    <div class="md:w-[45%] mb-4 md:mb-0 md:text-right">
                        <h3 class="text-xl font-bold text-cyber-ai">Phase 3: AI Analysis</h3>
                        <p class="text-cyber-muted mt-2 text-sm">Connect the AI Agent node (GPT-4o or Claude). Use the JSON system prompt to extract structured data (Category, Severity, Summary).</p>
                    </div>
                    <div class="absolute left-8 md:left-1/2 w-8 h-8 bg-cyber-bg border-4 border-cyber-ai rounded-full transform -translate-x-[1.2rem] md:-translate-x-1/2 flex items-center justify-center shadow-[0_0_15px_rgba(139,92,246,0.5)]">
                        <span class="text-xs font-bold text-cyber-ai">3</span>
                    </div>
                    <div class="md:w-[45%] pl-8 md:pl-0">
                        <span class="inline-block px-3 py-1 bg-cyber-card border border-cyber-ai text-cyber-ai text-xs rounded">n8n: AI Agent Node</span>
                    </div>
                </div>

                <!-- Phase 4 -->
                <div class="relative z-10 mb-16 md:flex md:justify-between items-center group">
                    <div class="md:w-[45%] order-2 md:order-1 pl-8 md:pl-0 md:text-right">
                        <span class="inline-block px-3 py-1 bg-cyber-card border border-cyber-safe text-cyber-safe text-xs rounded">n8n: Code Node</span>
                    </div>
                    <div class="absolute left-8 md:left-1/2 w-8 h-8 bg-cyber-bg border-4 border-cyber-safe rounded-full transform -translate-x-[1.2rem] md:-translate-x-1/2 flex items-center justify-center">
                        <span class="text-xs font-bold text-cyber-safe">4</span>
                    </div>
                    <div class="md:w-[45%] order-1 md:order-2 mb-4 md:mb-0">
                        <h3 class="text-xl font-bold text-cyber-text">Phase 4: Aggregation</h3>
                        <p class="text-cyber-muted mt-2 text-sm">Loop through the analyzed JSON items. Build an HTML string, grouping items by severity (put "Critical" at the top in red).</p>
                    </div>
                </div>

                <!-- Phase 5 -->
                <div class="relative z-10 md:flex md:justify-between items-center group">
                    <div class="md:w-[45%] mb-4 md:mb-0 md:text-right">
                        <h3 class="text-xl font-bold text-cyber-text">Phase 5: Delivery</h3>
                        <p class="text-cyber-muted mt-2 text-sm">Send the constructed HTML body via Gmail or format it into Block Kit blocks for a professional Slack notification.</p>
                    </div>
                    <div class="absolute left-8 md:left-1/2 w-8 h-8 bg-cyber-bg border-4 border-cyber-primary rounded-full transform -translate-x-[1.2rem] md:-translate-x-1/2 flex items-center justify-center">
                        <span class="text-xs font-bold text-cyber-primary">5</span>
                    </div>
                    <div class="md:w-[45%] pl-8 md:pl-0">
                        <span class="inline-block px-3 py-1 bg-cyber-card border border-cyber-primary text-cyber-primary text-xs rounded">n8n: Gmail/Slack Node</span>
                    </div>
                </div>

            </div>
        </section>

        <!-- Footer -->
        <footer class="border-t border-cyber-card pt-12 text-center">
            <h2 class="text-2xl font-bold text-cyber-text mb-4">Ready to automate your intelligence?</h2>
            <p class="text-cyber-muted mb-8 max-w-2xl mx-auto">
                Stop drowning in RSS feeds. Let n8n and AI do the heavy lifting so you can focus on remediation and strategy.
            </p>
            <div class="text-sm text-cyber-muted opacity-50">
                Generated based on the "Intelligent AI Digest for Security, Privacy, and Compliance" n8n tutorial.
            </div>
        </footer>

    </main>

    <!-- CHART CONFIGURATION -->
    <script>
        // Palette Variables for JS
        const colors = {
            primary: '#06b6d4', // Cyan
            ai: '#8b5cf6',      // Violet
            alert: '#ef4444',   // Red
            safe: '#10b981',    // Emerald
            card: '#1e293b',
            text: '#f8fafc',
            grid: 'rgba(148, 163, 184, 0.1)'
        };

        // --- HELPER: Label Wrapping for Chart.js ---
        function splitLabel(label, maxLength = 16) {
            if (label.length <= maxLength) return label;
            const words = label.split(' ');
            const lines = [];
            let currentLine = words[0];

            for (let i = 1; i < words.length; i++) {
                if (currentLine.length + 1 + words[i].length <= maxLength) {
                    currentLine += ' ' + words[i];
                } else {
                    lines.push(currentLine);
                    currentLine = words[i];
                }
            }
            lines.push(currentLine);
            return lines;
        }

        // --- GLOBAL CHART DEFAULTS ---
        Chart.defaults.color = colors.text;
        Chart.defaults.borderColor = colors.grid;
        Chart.defaults.font.family = "'Inter', sans-serif";

        // --- CHART 1: SOURCE DISTRIBUTION (Donut) ---
        const sourceCtx = document.getElementById('sourceChart').getContext('2d');
        // Labels: CISA, Hacker News, Bleeping Computer, IAPP, GDPR Info, NIST
        const sourceLabels = ["CISA Activity", "The Hacker News", "Bleeping Computer", "IAPP News", "GDPR Info", "NIST News"];
        const processedSourceLabels = sourceLabels.map(l => splitLabel(l));

        new Chart(sourceCtx, {
            type: 'doughnut',
            data: {
                labels: processedSourceLabels,
                datasets: [{
                    label: 'Feed Volume Share',
                    data: [25, 20, 20, 15, 10, 10], // Hypothetical distribution based on typical feed volume
                    backgroundColor: [
                        colors.alert, // CISA (Security)
                        '#f87171',    // Hacker News (Security Light)
                        '#b91c1c',    // Bleeping (Security Dark)
                        colors.ai,    // IAPP (Privacy)
                        colors.safe,  // GDPR (Compliance)
                        '#34d399'     // NIST (Tech/Gov)
                    ],
                    borderColor: colors.card,
                    borderWidth: 2,
                    hoverOffset: 10
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                cutout: '60%',
                plugins: {
                    legend: {
                        position: 'right',
                        labels: {
                            boxWidth: 12,
                            padding: 15,
                            font: { size: 11 }
                        }
                    },
                    tooltip: {
                        backgroundColor: colors.card,
                        titleColor: colors.primary,
                        bodyColor: colors.text,
                        borderColor: colors.primary,
                        borderWidth: 1,
                        padding: 10,
                        callbacks: {
                            title: function(tooltipItems) {
                                const item = tooltipItems[0];
                                let label = item.chart.data.labels[item.dataIndex];
                                return Array.isArray(label) ? label.join(' ') : label;
                            }
                        }
                    }
                }
            }
        });

        // --- CHART 2: SEVERITY SCORING (Bar) ---
        const severityCtx = document.getElementById('severityChart').getContext('2d');
        const severityLabels = ["Critical (Action Req)", "High (Review)", "Medium (Monitor)", "Low (Info Only)"];
        const processedSeverityLabels = severityLabels.map(l => splitLabel(l, 20));

        new Chart(severityCtx, {
            type: 'bar',
            data: {
                labels: processedSeverityLabels,
                datasets: [{
                    label: 'Articles Processed',
                    data: [2, 5, 12, 35], // 2 Critical, 5 High, 12 Medium, 35 Low (Noise)
                    backgroundColor: [
                        colors.alert,   // Critical -> Red
                        '#fbbf24',      // High -> Amber
                        colors.primary, // Medium -> Cyan
                        colors.safe     // Low -> Green/Safe
                    ],
                    borderRadius: 4,
                    barPercentage: 0.6
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                scales: {
                    y: {
                        beginAtZero: true,
                        grid: { color: colors.grid },
                        title: { display: true, text: 'Volume of Articles' }
                    },
                    x: {
                        grid: { display: false }
                    }
                },
                plugins: {
                    legend: { display: false },
                    tooltip: {
                        backgroundColor: colors.card,
                        titleColor: colors.primary,
                        bodyColor: colors.text,
                        borderColor: colors.ai,
                        borderWidth: 1,
                        padding: 10,
                        callbacks: {
                            title: function(tooltipItems) {
                                const item = tooltipItems[0];
                                let label = item.chart.data.labels[item.dataIndex];
                                return Array.isArray(label) ? label.join(' ') : label;
                            },
                            label: function(context) {
                                return ` ${context.raw} Articles`;
                            }
                        }
                    }
                }
            }
        });
    </script>
</body>
</html>
<!-- 
    CONFIRMATION:
    1. NO Mermaid JS used.
    2. NO SVG used (Unicode icons and CSS shapes used instead).
    3. Palette: "Cyber Watch" (Vibrant Dark Theme).
    4. Source Material: "Intelligent AI Digest for Security, Privacy, and Compliance Feeds" tutorial.
-->
