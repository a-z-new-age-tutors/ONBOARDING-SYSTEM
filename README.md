<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Onboarding System | Master Document</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;400;500;600;700&family=Inter:wght@300;400;500;600&display=swap" rel="stylesheet">
    <script src="https://unpkg.com/lucide@latest"></script>
    <style type="text/tailwindcss">
        @layer base {
            body {
                font-family: 'Inter', sans-serif;
                background: #0f172a;
                color: #e2e8f0;
            }
            h1, h2, h3, .display-font {
                font-family: 'Space Grotesk', sans-serif;
            }
        }
        @layer components {
            .stage-card {
                @apply relative bg-slate-800/50 backdrop-blur-xl border border-slate-700/50 rounded-2xl p-6 transition-all duration-500 hover:border-cyan-500/50 hover:shadow-2xl hover:shadow-cyan-500/10;
            }
            .stage-card.active {
                @apply border-cyan-500/50 shadow-2xl shadow-cyan-500/20 bg-slate-800/80;
            }
            .stage-card.completed {
                @apply border-emerald-500/30 bg-emerald-900/10;
            }
            .check-item {
                @apply flex items-start gap-3 p-3 rounded-lg transition-all duration-300 cursor-pointer hover:bg-slate-700/30;
            }
            .check-item:hover {
                @apply bg-slate-700/50;
            }
            .custom-checkbox {
                @apply w-5 h-5 rounded border-2 border-slate-500 flex items-center justify-center transition-all duration-300 flex-shrink-0 mt-0.5;
            }
            .custom-checkbox.checked {
                @apply bg-cyan-500 border-cyan-500;
            }
            .progress-bar {
                @apply h-2 bg-slate-700 rounded-full overflow-hidden;
            }
            .progress-fill {
                @apply h-full bg-gradient-to-r from-cyan-500 via-blue-500 to-purple-500 rounded-full transition-all duration-1000;
            }
            .status-badge {
                @apply inline-flex items-center gap-2 px-4 py-2 rounded-full text-sm font-medium uppercase tracking-wider;
            }
            .glow-text {
                text-shadow: 0 0 20px rgba(6, 182, 212, 0.5);
            }
            .grid-pattern {
                background-image: radial-gradient(circle at 1px 1px, rgba(255,255,255,0.05) 1px, transparent 0);
                background-size: 40px 40px;
            }
        }
    </style>
</head>
<body class="min-h-screen grid-pattern">
    <!-- Header -->
    <header class="sticky top-0 z-50 bg-slate-900/80 backdrop-blur-xl border-b border-slate-800">
        <div class="max-w-7xl mx-auto px-6 py-4">
            <div class="flex items-center justify-between">
                <div class="flex items-center gap-4">
                    <div class="w-12 h-12 rounded-xl bg-gradient-to-br from-cyan-500 to-blue-600 flex items-center justify-center shadow-lg shadow-cyan-500/20">
                        <i data-lucide="layers" class="w-6 h-6 text-white"></i>
                    </div>
                    <div>
                        <h1 class="text-2xl font-bold text-white tracking-tight">ONBOARDING SYSTEM</h1>
                        <p class="text-slate-400 text-sm">Master Document • Full Departmental Workflow</p>
                    </div>
                </div>
                <div class="flex items-center gap-4">
                    <div class="text-right">
                        <div class="text-3xl font-bold text-cyan-400" id="overall-progress">0%</div>
                        <div class="text-xs text-slate-500 uppercase tracking-wider">Complete</div>
                    </div>
                    <div class="w-32 progress-bar">
                        <div class="progress-fill" id="header-progress" style="width: 0%"></div>
                    </div>
                </div>
            </div>
        </div>
    </header>

    <!-- Main Content -->
    <main class="max-w-7xl mx-auto px-6 py-8">
        <!-- Intro Card -->
        <div class="mb-8 p-6 rounded-2xl bg-gradient-to-r from-slate-800/50 to-slate-900/50 border border-slate-700/50">
            <div class="flex items-start gap-4">
                <div class="w-10 h-10 rounded-lg bg-purple-500/20 flex items-center justify-center flex-shrink-0">
                    <i data-lucide="target" class="w-5 h-5 text-purple-400"></i>
                </div>
                <div>
                    <h2 class="text-lg font-semibold text-white mb-2">System Purpose</h2>
                    <p class="text-slate-400 leading-relaxed">This official onboarding structure is designed to track tutor progression, standardize recruitment and training workflow, and ensure full compliance and documentation across all departmental stages.</p>
                </div>
            </div>
        </div>

        <!-- Stages Grid -->
        <div class="grid gap-6" id="stages-container">
            <!-- Stage 1 -->
            <div class="stage-card" data-stage="1">
                <div class="flex items-start justify-between mb-4">
                    <div class="flex items-center gap-4">
                        <div class="w-14 h-14 rounded-2xl bg-gradient-to-br from-blue-500 to-cyan-600 flex items-center justify-center text-white font-bold text-xl shadow-lg shadow-blue-500/20">
                            01
                        </div>
                        <div>
                            <h3 class="text-xl font-bold text-white">Recruitment & Application Stage</h3>
                            <p class="text-cyan-400 text-sm font-medium">Recruitment Officer</p>
                        </div>
                    </div>
                    <div class="stage-progress text-2xl font-bold text-slate-600">0/8</div>
                </div>
                
                <div class="space-y-1 mb-4">
                    <div class="check-item" onclick="toggleCheck(this)">
                        <div class="custom-checkbox"><i data-lucide="check" class="w-3 h-3 text-white opacity-0 transition-opacity"></i></div>
                        <span class="text-slate-300">Recruitment officer sends application requirements to applicant</span>
                    </div>
                    <div class="check-item" onclick="toggleCheck(this)">
                        <div class="custom-checkbox"><i data-lucide="check" class="w-3 h-3 text-white opacity-0 transition-opacity"></i></div>
                        <span class="text-slate-300">Applicant downloads required applications/tools</span>
                    </div>
                    <div class="check-item" onclick="toggleCheck(this)">
                        <div class="custom-checkbox"><i data-lucide="check" class="w-3 h-3 text-white opacity-0 transition-opacity"></i></div>
                        <span class="text-slate-300">Applicant completes database form</span>
                    </div>
                    <div class="check-item" onclick="toggleCheck(this)">
                        <div class="custom-checkbox"><i data-lucide="check" class="w-3 h-3 text-white opacity-0 transition-opacity"></i></div>
                        <span class="text-slate-300">Applicant submits database screenshot</span>
                    </div>
                    <div class="check-item" onclick="toggleCheck(this)">
                        <div class="custom-checkbox"><i data-lucide="check" class="w-3 h-3 text-white opacity-0 transition-opacity"></i></div>
                        <span class="text-slate-300">Applicant submits policy acknowledgement form</span>
                    </div>
                    <div class="check-item" onclick="toggleCheck(this)">
                        <div class="custom-checkbox"><i data-lucide="check" class="w-3 h-3 text-white opacity-0 transition-opacity"></i></div>
                        <span class="text-slate-300">Applicant submits screenshots of downloaded applications</span>
                    </div>
                    <div class="check-item" onclick="toggleCheck(this)">
                        <div class="custom-checkbox"><i data-lucide="check" class="w-3 h-3 text-white opacity-0 transition-opacity"></i></div>
                        <span class="text-slate-300">Applicant submits screenshots of agency social media follows</span>
                    </div>
                    <div class="mt-4 p-3 bg-slate-900/50 rounded-lg border border-slate-700/50">
                        <p class="text-sm text-slate-400 mb-2 font-medium">Interview Process:</p>
                        <div class="check-item" onclick="toggleCheck(this)">
                            <div class="custom-checkbox"><i data-lucide="check" class="w-3 h-3 text-white opacity-0 transition-opacity"></i></div>
                            <span class="text-slate-300">Interview scheduled</span>
                        </div>
                        <div class="check-item" onclick="toggleCheck(this)">
                            <div class="custom-checkbox"><i data-lucide="check" class="w-3 h-3 text-white opacity-0 transition-opacity"></i></div>
                            <span class="text-slate-300">Interview conducted</span>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Stage 2 -->
            <div class="stage-card" data-stage="2">
                <div class="flex items-start justify-between mb-4">
                    <div class="flex items-center gap-4">
                        <div class="w-14 h-14 rounded-2xl bg-gradient-to-br from-purple-500 to-pink-600 flex items-center justify-center text-white font-bold text-xl shadow-lg shadow-purple-500/20">
                            02
                        </div>
                        <div>
                            <h3 class="text-xl font-bold text-white">Director Engagement Stage</h3>
                            <p class="text-purple-400 text-sm font-medium">Recruitment Officer</p>
                        </div>
                    </div>
                    <div class="stage-progress text-2xl font-bold text-slate-600">0/2</div>
                </div>
                
                <div class="space-y-1 mb-4">
                    <div class="check-item" onclick="toggleCheck(this)">
                        <div class="custom-checkbox"><i data-lucide="check" class="w-3 h-3 text-white opacity-0 transition-opacity"></i></div>
                        <span class="text-slate-300">Post-interview video reviewed</span>
                    </div>
                    <div class="check-item" onclick="toggleCheck(this)">
                        <div class="custom-checkbox"><i data-lucide="check" class="w-3 h-3 text-white opacity-0 transition-opacity"></i></div>
                        <span class="text-slate-300">Call conducted with Director</span>
                    </div>
                </div>
                
                <div class="status-badge bg-purple-500/10 text-purple-400 border border-purple-500/20">
                    <i data-lucide="award" class="w-4 h-4"></i>
                    STATUS: DIRECTOR ENGAGEMENT COMPLETED
                </div>
            </div>

            <!-- Stage 3 -->
            <div class="stage-card" data-stage="3">
                <div class="flex items-start justify-between mb-4">
                    <div class="flex items-center gap-4">
                        <div class="w-14 h-14 rounded-2xl bg-gradient-to-br from-orange-500 to-red-600 flex items-center justify-center text-white font-bold text-xl shadow-lg shadow-orange-500/20">
                            03
                        </div>
                        <div>
                            <h3 class="text-xl font-bold text-white">Orientation Entry Stage</h3>
                            <p class="text-orange-400 text-sm font-medium">Orientation Unit</p>
                        </div>
                    </div>
                    <div class="stage-progress text-2xl font-bold text-slate-600">0/8</div>
                </div>
                
                <div class="space-y-1 mb-4">
                    <div class="check-item" onclick="toggleCheck(this)">
                        <div class="custom-checkbox"><i data-lucide="check" class="w-3 h-3 text-white opacity-0 transition-opacity"></i></div>
                        <span class="text-slate-300">Tutor added to orientation platform</span>
                    </div>
                    <div class="check-item" onclick="toggleCheck(this)">
                        <div class="custom-checkbox"><i data-lucide="check" class="w-3 h-3 text-white opacity-0 transition-opacity"></i></div>
                        <span class="text-slate-300">Welcome message received</span>
                    </div>
                    <div class="check-item" onclick="toggleCheck(this)">
                        <div class="custom-checkbox"><i data-lucide="check" class="w-3 h-3 text-white opacity-0 transition-opacity"></i></div>
                        <span class="text-slate-300">App usage video watched</span>
                    </div>
                    <div class="check-item" onclick="toggleCheck(this)">
                        <div class="custom-checkbox"><i data-lucide="check" class="w-3 h-3 text-white opacity-0 transition-opacity"></i></div>
                        <span class="text-slate-300">Virtual orientation attended</span>
                    </div>
                    <div class="check-item" onclick="toggleCheck(this)">
                        <div class="custom-checkbox"><i data-lucide="check" class="w-3 h-3 text-white opacity-0 transition-opacity"></i></div>
                        <span class="text-slate-300">Agency structure understood</span>
                    </div>
                    <div class="check-item" onclick="toggleCheck(this)">
                        <div class="custom-checkbox"><i data-lucide="check" class="w-3 h-3 text-white opacity-0 transition-opacity"></i></div>
                        <span class="text-slate-300">Added to probationary group</span>
                    </div>
                    <div class="check-item" onclick="toggleCheck(this)">
                        <div class="custom-checkbox"><i data-lucide="check" class="w-3 h-3 text-white opacity-0 transition-opacity"></i></div>
                        <span class="text-slate-300">Probationary letter received</span>
                    </div>
                    <div class="check-item" onclick="toggleCheck(this)">
                        <div class="custom-checkbox"><i data-lucide="check" class="w-3 h-3 text-white opacity-0 transition-opacity"></i></div>
                        <span class="text-slate-300">Probationary letter submitted</span>
                    </div>
                </div>
                
                <div class="status-badge bg-orange-500/10 text-orange-400 border border-orange-500/20">
                    <i data-lucide="compass" class="w-4 h-4"></i>
                    STATUS: ORIENTATION STAGE COMPLETED
                </div>
            </div>

            <!-- Stage 4 -->
            <div class="stage-card" data-stage="4">
                <div class="flex items-start justify-between mb-4">
                    <div class="flex items-center gap-4">
                        <div class="w-14 h-14 rounded-2xl bg-gradient-to-br from-teal-500 to-emerald-600 flex items-center justify-center text-white font-bold text-xl shadow-lg shadow-teal-500/20">
                            04
                        </div>
                        <div>
                            <h3 class="text-xl font-bold text-white">Quality Assurance & Guidance Mentorship</h3>
                            <p class="text-teal-400 text-sm font-medium">QAG Officer</p>
                        </div>
                    </div>
                    <div class="stage-progress text-2xl font-bold text-slate-600">0/3</div>
                </div>
                
                <div class="space-y-1 mb-4">
                    <div class="check-item" onclick="toggleCheck(this)">
                        <div class="custom-checkbox"><i data-lucide="check" class="w-3 h-3 text-white opacity-0 transition-opacity"></i></div>
                        <span class="text-slate-300">Session 1 scheduled</span>
                    </div>
                    <div class="check-item" onclick="toggleCheck(this)">
                        <div class="custom-checkbox"><i data-lucide="check" class="w-3 h-3 text-white opacity-0 transition-opacity"></i></div>
                        <span class="text-slate-300">Session 2 scheduled</span>
                    </div>
                    <div class="check-item" onclick="toggleCheck(this)">
                        <div class="custom-checkbox"><i data-lucide="check" class="w-3 h-3 text-white opacity-0 transition-opacity"></i></div>
                        <span class="text-slate-300">Session 3 scheduled</span>
                    </div>
                </div>
                
                <div class="status-badge bg-teal-500/10 text-teal-400 border border-teal-500/20">
                    <i data-lucide="shield-check" class="w-4 h-4"></i>
                    STATUS: MENTORSHIP COMPLETED
                </div>
            </div>

            <!-- Stage 5 -->
            <div class="stage-card" data-stage="5">
                <div class="flex items-start justify-between mb-4">
                    <div class="flex items-center gap-4">
                        <div class="w-14 h-14 rounded-2xl bg-gradient-to-br from-yellow-500 to-amber-600 flex items-center justify-center text-white font-bold text-xl shadow-lg shadow-yellow-500/20">
                            05
                        </div>
                        <div>
                            <h3 class="text-xl font-bold text-white">Physical Orientation Stage</h3>
                            <p class="text-yellow-400 text-sm font-medium">Orientation Unit</p>
                        </div>
                    </div>
                    <div class="stage-progress text-2xl font-bold text-slate-600">0/3</div>
                </div>
                
                <div class="space-y-1 mb-4">
                    <div class="check-item" onclick="toggleCheck(this)">
                        <div class="custom-checkbox"><i data-lucide="check" class="w-3 h-3 text-white opacity-0 transition-opacity"></i></div>
                        <span class="text-slate-300">Physical orientation attended</span>
                    </div>
                    <div class="check-item" onclick="toggleCheck(this)">
                        <div class="custom-checkbox"><i data-lucide="check" class="w-3 h-3 text-white opacity-0 transition-opacity"></i></div>
                        <span class="text-slate-300">Orientation exercise completed</span>
                    </div>
                    <div class="check-item" onclick="toggleCheck(this)">
                        <div class="custom-checkbox"><i data-lucide="check" class="w-3 h-3 text-white opacity-0 transition-opacity"></i></div>
                        <span class="text-slate-300">Passed / Retake required</span>
                    </div>
                </div>
                
                <div class="status-badge bg-yellow-500/10 text-yellow-400 border border-yellow-500/20">
                    <i data-lucide="map-pin" class="w-4 h-4"></i>
                    STATUS: PHYSICAL ORIENTATION COMPLETED
                </div>
            </div>

            <!-- Stage 6 -->
            <div class="stage-card" data-stage="6">
                <div class="flex items-start justify-between mb-4">
                    <div class="flex items-center gap-4">
                        <div class="w-14 h-14 rounded-2xl bg-gradient-to-br from-indigo-500 to-violet-600 flex items-center justify-center text-white font-bold text-xl shadow-lg shadow-indigo-500/20">
                            06
                        </div>
                        <div>
                            <h3 class="text-xl font-bold text-white">Employment Confirmation Stage</h3>
                            <p class="text-indigo-400 text-sm font-medium">Admin Officer</p>
                        </div>
                    </div>
                    <div class="stage-progress text-2xl font-bold text-slate-600">0/2</div>
                </div>
                
                <div class="space-y-1 mb-4">
                    <div class="check-item" onclick="toggleCheck(this)">
                        <div class="custom-checkbox"><i data-lucide="check" class="w-3 h-3 text-white opacity-0 transition-opacity"></i></div>
                        <span class="text-slate-300">Employment documents received</span>
                    </div>
                    <div class="check-item" onclick="toggleCheck(this)">
                        <div class="custom-checkbox"><i data-lucide="check" class="w-3 h-3 text-white opacity-0 transition-opacity"></i></div>
                        <span class="text-slate-300">Tutor officially recognized as staff</span>
                    </div>
                </div>
                
                <div class="status-badge bg-indigo-500/10 text-indigo-400 border border-indigo-500/20">
                    <i data-lucide="briefcase" class="w-4 h-4"></i>
                    STATUS: EMPLOYMENT CONFIRMED
                </div>
            </div>

            <!-- Stage 7 -->
            <div class="stage-card" data-stage="7">
                <div class="flex items-start justify-between mb-4">
                    <div class="flex items-center gap-4">
                        <div class="w-14 h-14 rounded-2xl bg-gradient-to-br from-emerald-500 to-green-600 flex items-center justify-center text-white font-bold text-xl shadow-lg shadow-emerald-500/20">
                            07
                        </div>
                        <div>
                            <h3 class="text-xl font-bold text-white">Administrative Integration & Platform Transfer</h3>
                            <p class="text-emerald-400 text-sm font-medium">System Operations</p>
                        </div>
                    </div>
                    <div class="stage-progress text-2xl font-bold text-slate-600">0/3</div>
                </div>
                
                <div class="space-y-1 mb-4">
                    <div class="check-item" onclick="toggleCheck(this)">
                        <div class="custom-checkbox"><i data-lucide="check" class="w-3 h-3 text-white opacity-0 transition-opacity"></i></div>
                        <span class="text-slate-300">Removed from orientation platform</span>
                    </div>
                    <div class="check-item" onclick="toggleCheck(this)">
                        <div class="custom-checkbox"><i data-lucide="check" class="w-3 h-3 text-white opacity-0 transition-opacity"></i></div>
                        <span class="text-slate-300">Added to agency groups</span>
                    </div>
                    <div class="check-item" onclick="toggleCheck(this)">
                        <div class="custom-checkbox"><i data-lucide="check" class="w-3 h-3 text-white opacity-0 transition-opacity"></i></div>
                        <span class="text-slate-300">Documents verified</span>
                    </div>
                </div>
            </div>
        </div>

        <!-- Final Status -->
        <div class="mt-8 p-8 rounded-2xl bg-gradient-to-r from-emerald-900/30 to-cyan-900/30 border border-emerald-500/30 text-center relative overflow-hidden" id="final-status">
            <div class="absolute inset-0 bg-gradient-to-r from-emerald-500/5 to-cyan-500/5"></div>
            <div class="relative z-10">
                <div class="w-16 h-16 rounded-full bg-emerald-500/20 flex items-center justify-center mx-auto mb-4">
                    <i data-lucide="flag" class="w-8 h-8 text-emerald-400"></i>
                </div>
                <h2 class="text-2xl font-bold text-white mb-2">FINAL STATUS</h2>
                <p class="text-emerald-400 text-lg font-semibold tracking-wider">FULL ONBOARDING SYSTEM COMPLETED</p>
            </div>
        </div>
    </main>

    <script>
        // Initialize Lucide icons
        lucide.createIcons();

        function toggleCheck(element) {
            const checkbox = element.querySelector('.custom-checkbox');
            const checkIcon = checkbox.querySelector('svg');
            const isChecked = checkbox.classList.contains('checked');
            
            if (isChecked) {
                checkbox.classList.remove('checked');
                checkIcon.style.opacity = '0';
            } else {
                checkbox.classList.add('checked');
                checkIcon.style.opacity = '1';
            }
            
            updateProgress();
        }

        function updateProgress() {
            const stages = document.querySelectorAll('.stage-card');
            let totalItems = 0;
            let checkedItems = 0;
            
            stages.forEach(stage => {
                const checkItems = stage.querySelectorAll('.check-item');
                const stageTotal = checkItems.length;
                const stageChecked = stage.querySelectorAll('.custom-checkbox.checked').length;
                
                totalItems += stageTotal;
                checkedItems += stageChecked;
                
                // Update stage counter
                const counter = stage.querySelector('.stage-progress');
                if (counter) {
                    counter.textContent = `${stageChecked}/${stageTotal}`;
                    
                    if (stageChecked === stageTotal && stageTotal > 0) {
                        counter.classList.remove('text-slate-600');
                        counter.classList.add('text-emerald-400');
                        stage.classList.add('completed');
                    } else {
                        counter.classList.add('text-slate-600');
                        counter.classList.remove('text-emerald-400');
                        stage.classList.remove('completed');
                    }
                }
            });
            
            const percentage = totalItems > 0 ? Math.round((checkedItems / totalItems) * 100) : 0;
            document.getElementById('overall-progress').textContent = `${percentage}%`;
            document.getElementById('header-progress').style.width = `${percentage}%`;
            
            // Animate final status if 100%
            const finalStatus = document.getElementById('final-status');
            if (percentage === 100) {
                finalStatus.classList.add('ring-2', 'ring-emerald-500', 'ring-offset-2', 'ring-offset-slate-900');
            } else {
                finalStatus.classList.remove('ring-2', 'ring-emerald-500', 'ring-offset-2', 'ring-offset-slate-900');
            }
        }

        // Add intersection observer for scroll animations
        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -50px 0px'
        };

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.style.opacity = '1';
                    entry.target.style.transform = 'translateY(0)';
                }
            });
        }, observerOptions);

        // Initialize cards with animation
        document.querySelectorAll('.stage-card').forEach((card, index) => {
            card.style.opacity = '0';
            card.style.transform = 'translateY(20px)';
            card.style.transition = `opacity 0.6s ease ${index * 0.1}s, transform 0.6s ease ${index * 0.1}s`;
            observer.observe(card);
        });

        // Initialize final status
        const finalStatus = document.getElementById('final-status');
        finalStatus.style.opacity = '0';
        finalStatus.style.transform = 'translateY(20px)';
        finalStatus.style.transition = 'opacity 0.6s ease 0.7s, transform 0.6s ease 0.7s';
        observer.observe(finalStatus);
    </script>
</body>
</html>
