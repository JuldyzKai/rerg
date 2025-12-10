<!DOCTYPE html>
<html lang="kk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ақ боз үй - Портреттік талдау | Смағұл Елубай</title>
    <meta name="description" content="Смағұл Елубайдың Ақ боз үй романындағы портреттік элементтерді автоматты тану жүйесі">
    <meta name="keywords" content="Ақ боз үй, Смағұл Елубай, портреттік талдау, қазақ әдебиеті, соматема, вестема, кинетема">
    
    <!-- Bootstrap CSS -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet">
    
    <!-- Chart.js -->
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    
    <!-- Font Awesome -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    
    <style>
        :root {
            --somatema-color: #dc3545;
            --vestema-color: #0d6efd;
            --kinetema-color: #198754;
        }
        
        .somatema { 
            border-left: 4px solid var(--somatema-color); 
            background-color: #fff5f5; 
        }
        .vestema { 
            border-left: 4px solid var(--vestema-color); 
            background-color: #f0f8ff; 
        }
        .kinetema { 
            border-left: 4px solid var(--kinetema-color); 
            background-color: #f0fff4; 
        }
        
        .annotation { 
            transition: all 0.3s ease; 
            margin-bottom: 1rem;
        }
        .annotation:hover { 
            transform: translateX(5px); 
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
        }
        
        .stats-card { 
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); 
            color: white; 
        }
        
        .hero-section {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 3rem 0;
            margin-bottom: 2rem;
        }
        
        .feature-icon {
            font-size: 2rem;
            margin-bottom: 1rem;
            color: #667eea;
        }
        
        @media (max-width: 768px) {
            .hero-section h1 {
                font-size: 1.8rem;
            }
            .card-body {
                padding: 1rem;
            }
        }
        
        /* Print styles */
        @media print {
            .no-print { display: none !important; }
            .card { border: 1px solid #000 !important; }
        }
    </style>
</head>
<body>
    <!-- Навигация -->
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
        <div class="container">
            <a class="navbar-brand" href="#">
                <i class="fas fa-book-open me-2"></i>
                Ақ боз үй талдауы
            </a>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarNav">
                <ul class="navbar-nav ms-auto">
                    <li class="nav-item">
                        <a class="nav-link" href="#about">Жоба туралы</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" href="#how-to-use">Қолдану</a>
                    </li>
                    <li class="nav-item">
                        <button class="btn btn-outline-light btn-sm ms-2 no-print" onclick="window.print()">
                            <i class="fas fa-print me-1"></i>Басып шығару
                        </button>
                    </li>
                </ul>
            </div>
        </div>
    </nav>

    <!-- Басты бөлім -->
    <div class="hero-section">
        <div class="container text-center">
            <h1 class="display-4 fw-bold mb-3">«Ақ боз үй» романын портреттік талдау</h1>
            
        </div>
    </div>

    <div class="container" id="analyzer">
        <div class="row">
            <!-- Сол жақ баған -->
            <div class="col-lg-6 mb-4">
                <!-- Мәтін енгізу -->
                <div class="card shadow-lg border-0">
                    <div class="card-header bg-primary text-white py-3">
                        <h4 class="mb-0"><i class="fas fa-edit me-2"></i>Мәтін енгізу</h4>
                    </div>
                    <div class="card-body">
                        <textarea id="textInput" rows="12" class="form-control form-control-lg" 
                                  placeholder="Мәтінді мына жерге енгізіңіз... 
Мысалы: Хансұлудың шашы бұрқырап, көзі мойыл, үстінде қырмызы қамзол киген..."></textarea>
                        <div class="mt-3 d-grid gap-2 d-md-flex justify-content-md-end">
                            <button onclick="clearText()" class="btn btn-outline-danger">
                                <i class="fas fa-trash me-1"></i>Тазарту
                            </button>
                            <button onclick="loadSampleText()" class="btn btn-outline-secondary">
                                <i class="fas fa-file-alt me-1"></i>Үлгі мәтін
                            </button>
                            <button onclick="analyzeText()" class="btn btn-success btn-lg">
                                <i class="fas fa-search me-1"></i>ТАЛДАУ
                            </button>
                        </div>
                    </div>
                </div>

                <!-- Анықтамалар -->
                <div class="card shadow-sm border-0 mt-4">
                    <div class="card-header bg-warning text-dark py-3">
                        <h5 class="mb-0"><i class="fas fa-info-circle me-2"></i>Анықтамалар</h5>
                    </div>
                    <div class="card-body">
                        <div class="row text-center">
                            <div class="col-md-4 mb-3">
                                <div class="feature-icon">
                                    <i class="fas fa-user" style="color: var(--somatema-color);"></i>
                                </div>
                                <span class="badge bg-danger mb-2">SOMATEMA</span>
                                <p class="small mb-1"><strong>Дене мүшелері</strong></p>
                                <small class="text-muted">шаш, көз, бет, қол, иық</small>
                            </div>
                            <div class="col-md-4 mb-3">
                                <div class="feature-icon">
                                    <i class="fas fa-tshirt" style="color: var(--vestema-color);"></i>
                                </div>
                                <span class="badge bg-primary mb-2">VESTEMA</span>
                                <p class="small mb-1"><strong>Киім-кешек</strong></p>
                                <small class="text-muted">бөрік, шапан, орамал, етік</small>
                            </div>
                            <div class="col-md-4 mb-3">
                                <div class="feature-icon">
                                    <i class="fas fa-running" style="color: var(--kinetema-color);"></i>
                                </div>
                                <span class="badge bg-success mb-2">KINETEMA</span>
                                <p class="small mb-1"><strong>Қимыл-мінез</strong></p>
                                <small class="text-muted">сілкіп, күлді, жүрді, бүлкілдеп</small>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Жоба туралы -->
                <div class="card shadow-sm border-0 mt-4" id="about">
                    <div class="card-header bg-info text-white py-3">
                        <h5 class="mb-0"><i class="fas fa-project-diagram me-2"></i>Жоба туралы</h5>
                    </div>
                    <div class="card-body">
                        <p>Бұл жоба Смағұл Елубайдың «Ақ боз үй» романындағы портреттік элементтерді автоматты түрде тануға арналған.</p>
                        <div class="small text-muted">
                            <strong>Әзірлеуші:</strong> Еркежан жобасы<br>
                            <strong>Мақсаты:</strong> Әдебиеттанудың заманауи әдістерін қолдану
                        </div>
                    </div>
                </div>
            </div>

            <!-- Оң жақ баған -->
            <div class="col-lg-6">
                <!-- Статистика -->
                <div class="card shadow-lg border-0 mb-4">
                    <div class="card-header stats-card py-3">
                        <h4 class="mb-0"><i class="fas fa-chart-pie me-2"></i>Статистика</h4>
                    </div>
                    <div class="card-body">
                        <canvas id="statisticsChart" height="250"></canvas>
                    </div>
                </div>

                <!-- Нәтижелер -->
                <div class="card shadow-lg border-0">
                    <div class="card-header bg-success text-white py-3">
                        <div class="d-flex justify-content-between align-items-center">
                            <h4 class="mb-0"><i class="fas fa-search me-2"></i>Талдау нәтижелері</h4>
                            <span id="resultCount" class="badge bg-light text-dark fs-6">0 табылды</span>
                        </div>
                    </div>
                    <div class="card-body" style="max-height: 500px; overflow-y: auto;">
                        <div id="annotationList">
                            <div class="text-center text-muted py-5">
                                <div class="mb-3">
                                    <i class="fas fa-search fa-3x opacity-25"></i>
                                </div>
                                <h5>Нәтижелер осы жерде көрсетіледі</h5>
                                <p>Мәтінді енгізіп, "ТАЛДАУ" батырмасын басыңыз</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Қолдану нұсқаулығы -->
        <div class="card shadow-sm border-0 mt-5" id="how-to-use">
            <div class="card-header bg-secondary text-white py-3">
                <h5 class="mb-0"><i class="fas fa-question-circle me-2"></i>Қолдану нұсқаулығы</h5>
            </div>
            <div class="card-body">
                <div class="row">
                    <div class="col-md-6">
                        <h6>1. Мәтін енгізу</h6>
                        <p class="small">Үлгі мәтінді жүктеу үшін "Үлгі мәтін" батырмасын басыңыз немесе өз мәтініңізді енгізіңіз.</p>
                    </div>
                    <div class="col-md-6">
                        <h6>2. Талдау</h6>
                        <p class="small">"ТАЛДАУ" батырмасын басып, портреттік элементтерді табыңыз.</p>
                    </div>
                    <div class="col-md-6">
                        <h6>3. Нәтижелерді қарау</h6>
                        <p class="small">Табылған элементтер түрлі-түсті белгішелермен көрсетіледі.</p>
                    </div>
                    <div class="col-md-6">
                        <h6>4. Статистика</h6>
                        <p class="small">График арқылы элементтердің таралуын бақылаңыз.</p>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Футер -->
    <footer class="bg-dark text-light mt-5 py-4">
        <div class="container text-center">
            <p class="mb-0">«Ақ боз үй» портреттік талдау жүйесі &copy; 2024</p>
            <small class="text-muted">Барлық браузерлерде жұмыс істейді | Mobile-friendly | Offline қолдауы</small>
        </div>
    </footer>

    <script>
        // Сөздіктер
        const dictionaries = {
            somatema: {
                "ШАШ": ["шаш", "сақал", "көкбурыл", "аппақ", "бұрқырап", "сақал-шаш", "шашы", "шашын", "кірпік", "мұрт", "шашбау"],
                "КӨЗ": ["көз", "мойыл", "шақырайған", "бітіккөз", "ала көз", "көз қиығы", "көзі", "көзін", "көздері", "көз жасы"],
                "БЕТ": ["бет", "тарғыл", "томпақ", "шұбар", "жалпақ", "бет-ауыз", "беті", "бетін", "бетіне", "беталып"],
                "ҚОЛ": ["қол", "аяқ", "етжеңді", "тегеурінді", "қол сілтеді", "қолы", "қолын", "қолдары", "қол ұшын"],
                "ИЫҚ": ["иық", "кең иық", "иығын қомдап", "иығы", "иығын", "иықтары", "иықтан"]
            },
            vestema: {
                "КИІМ": ["бөрік", "шапан", "орамал", "етік", "камзол", "тымақ", "кілемше", "тон", "шекпен", "ішік", "бешпет"],
                "БЕЛДІК": ["белдік", "белбеу", "түрме", "шолпы", "шашбау", "белді", "белі", "белбеуі", "бел бау"]
            },
            kinetema: {
                "ҚИМЫЛ": ["сілкіп", "бүлкілдеп", "тарбандап", "жыртып", "шалпылдап", "қозғалды", "жүрді", "отырды", "тұрды", "жөтелді"],
                "МІНЕЗ": ["шақырайған", "миыл", "ала", "бітік", "күлкісі", "күлді", "жылады", "күлімсіреді", "жыбырлады"]
            }
        };

        let myChart = null;

        // Талдау функциясы
        function analyzeText() {
            const text = document.getElementById('textInput').value.trim();
            if (!text) {
                showAlert('Мәтінді енгізіңіз!', 'warning');
                return;
            }

            showLoading();
            
            // Жасанды кідірту
            setTimeout(() => {
                try {
                    const results = performAnalysis(text);
                    displayResults(results);
                    showAlert('Талдау аяқталды! ' + results.length + ' элемент табылды.', 'success');
                } catch (error) {
                    console.error('Талдау қатесі:', error);
                    showAlert('Талдау кезінде қате орын алды.', 'danger');
                }
            }, 800);
        }

        // Талдау жүргізу
        function performAnalysis(text) {
            const annotations = [];
            
            for (const [type, categories] of Object.entries(dictionaries)) {
                for (const [category, words] of Object.entries(categories)) {
                    for (const word of words) {
                        const regex = new RegExp(word, 'gi');
                        let match;
                        while ((match = regex.exec(text)) !== null) {
                            annotations.push({
                                wordPhrase: match[0],
                                annotationType: type.toUpperCase(),
                                category: category,
                                startPos: match.index,
                                endPos: match.index + match[0].length,
                                context: getContext(text, match.index, match[0].length)
                            });
                        }
                    }
                }
            }
            
            annotations.sort((a, b) => a.startPos - b.startPos);
            return annotations;
        }

        // Контекст алу
        function getContext(text, position, length) {
            const start = Math.max(0, position - 30);
            const end = Math.min(text.length, position + length + 30);
            let context = text.substring(start, end);
            
            if (start > 0) context = '...' + context;
            if (end < text.length) context = context + '...';
            
            return context;
        }

        // Нәтижелерді көрсету
        function displayResults(annotations) {
            const annotationList = document.getElementById('annotationList');
            const resultCount = document.getElementById('resultCount');
            
            resultCount.textContent = `${annotations.length} табылды`;
            
            if (annotations.length === 0) {
                annotationList.innerHTML = `
                    <div class="alert alert-warning text-center">
                        <h5><i class="fas fa-exclamation-triangle me-2"></i>Портреттік элементтер табылмады</h5>
                        <p class="mb-0">Мәтінде портреттік сипаттамалар жоқ немесе басқа мәтін енгізіп көріңіз</p>
                    </div>
                `;
                updateChart({});
                return;
            }

            let html = '';
            annotations.forEach((annotation, index) => {
                const colorClass = getAnnotationColor(annotation.annotationType);
                const typeName = getTypeName(annotation.annotationType);
                
                html += `
                    <div class="annotation card mb-3 ${colorClass}">
                        <div class="card-body">
                            <div class="d-flex justify-content-between align-items-start mb-2">
                                <div>
                                    <span class="badge ${getBadgeColor(annotation.annotationType)} fs-6">
                                        ${annotation.annotationType}
                                    </span>
                                    <span class="badge bg-secondary ms-1">${annotation.category}</span>
                                </div>
                                <small class="text-muted">#${index + 1}</small>
                            </div>
                            <h5 class="card-title text-primary">
                                <i class="fas fa-quote-left me-1 text-muted"></i>
                                ${annotation.wordPhrase}
                                <i class="fas fa-quote-right ms-1 text-muted"></i>
                            </h5>
                            <p class="card-text mb-2">
                                <small class="text-muted">
                                    <strong>Контекст:</strong> ${annotation.context}
                                </small>
                            </p>
                            <div class="d-flex justify-content-between align-items-center">
                                <small class="text-muted">
                                    <i class="fas fa-map-marker-alt me-1"></i>Позиция: ${annotation.startPos}-${annotation.endPos}
                                </small>
                                <small class="text-muted">${typeName}</small>
                            </div>
                        </div>
                    </div>
                `;
            });
            
            annotationList.innerHTML = html;
            updateChart(calculateStatistics(annotations));
        }

        // Статистиканы есептеу
        function calculateStatistics(annotations) {
            const stats = {};
            annotations.forEach(annotation => {
                stats[annotation.annotationType] = (stats[annotation.annotationType] || 0) + 1;
            });
            return stats;
        }

        // Графикті жаңарту
        function updateChart(statistics) {
            const ctx = document.getElementById('statisticsChart').getContext('2d');
            
            if (myChart) {
                myChart.destroy();
            }

            const labels = Object.keys(statistics);
            const data = Object.values(statistics);
            
            if (labels.length === 0) {
                myChart = new Chart(ctx, {
                    type: 'doughnut',
                    data: {
                        labels: ['Табылмады'],
                        datasets: [{
                            data: [1],
                            backgroundColor: ['#6c757d']
                        }]
                    },
                    options: getChartOptions('Ештеңе табылмады')
                });
                return;
            }

            const colors = {
                'SOMATEMA': '#dc3545',
                'VESTEMA': '#0d6efd', 
                'KINETEMA': '#198754'
            };

            myChart = new Chart(ctx, {
                type: 'doughnut',
                data: {
                    labels: labels,
                    datasets: [{
                        data: data,
                        backgroundColor: labels.map(label => colors[label] || '#6c757d'),
                        borderWidth: 3,
                        borderColor: '#fff'
                    }]
                },
                options: getChartOptions('Портреттік элементтердің таралуы')
            });
        }

        // График опциялары
        function getChartOptions(title) {
            return {
                responsive: true,
                maintainAspectRatio: false,
                plugins: {
                    legend: {
                        position: 'bottom',
                        labels: { font: { size: 14 } }
                    },
                    title: {
                        display: true,
                        text: title,
                        font: { size: 16, weight: 'bold' }
                    },
                    tooltip: {
                        callbacks: {
                            label: function(context) {
                                const label = context.label;
                                const value = context.parsed;
                                const total = context.dataset.data.reduce((a, b) => a + b, 0);
                                const percentage = Math.round((value / total) * 100);
                                return `${label}: ${value} (${percentage}%)`;
                            }
                        }
                    }
                }
            };
        }

        // Көмекші функциялар
        function getAnnotationColor(type) {
            const colors = {
                'SOMATEMA': 'somatema',
                'VESTEMA': 'vestema', 
                'KINETEMA': 'kinetema'
            };
            return colors[type] || '';
        }

        function getBadgeColor(type) {
            const colors = {
                'SOMATEMA': 'bg-danger',
                'VESTEMA': 'bg-primary',
                'KINETEMA': 'bg-success'
            };
            return colors[type] || 'bg-secondary';
        }

        function getTypeName(type) {
            const names = {
                'SOMATEMA': 'Дене мүшесі',
                'VESTEMA': 'Киім-кешек',
                'KINETEMA': 'Қимыл-мінез'
            };
            return names[type] || type;
        }

        function showLoading() {
            const annotationList = document.getElementById('annotationList');
            annotationList.innerHTML = `
                <div class="text-center py-4">
                    <div class="spinner-border text-primary" style="width: 3rem; height: 3rem;"></div>
                    <h5 class="mt-3 text-primary">Талдау жүріп жатыр...</h5>
                    <p class="text-muted">Мәтіндегі портреттік элементтер ізделуде</p>
                </div>
            `;
        }

        function showAlert(message, type = 'info') {
            // Ескі хабарландыруларды жою
            const oldAlerts = document.querySelectorAll('.alert-dismissible');
            oldAlerts.forEach(alert => alert.remove());
            
            const alert = document.createElement('div');
            alert.className = `alert alert-${type} alert-dismissible fade show position-fixed`;
            alert.style.cssText = 'top: 80px; right: 20px; z-index: 1050; min-width: 300px;';
            alert.innerHTML = `
                <i class="fas fa-${getAlertIcon(type)} me-2"></i>
                ${message}
                <button type="button" class="btn-close" data-bs-dismiss="alert"></button>
            `;
            document.body.appendChild(alert);
            
            setTimeout(() => {
                if (alert.parentNode) {
                    alert.remove();
                }
            }, 5000);
        }

        function getAlertIcon(type) {
            const icons = {
                'success': 'check-circle',
                'warning': 'exclamation-triangle',
                'danger': 'times-circle',
                'info': 'info-circle'
            };
            return icons[type] || 'info-circle';
        }

        // Мәтінді тазарту
        function clearText() {
            document.getElementById('textInput').value = '';
            showAlert('Мәтін тазартылды!', 'info');
        }

        // Үлгі мәтін
        function loadSampleText() {
            const sampleText = `Хансұлудың портреті -- Пахраддин мырзаның маңдайға біткен жалғызы. Тал шыбықша бұралып жетіліп келеді. Сұлу десең сұлу, ерке десең ерке. Қаракерин сылаң-сылаң желдіріп, төбесінде үкісі бұлғалақтаған камшат бөркі, үстінде -- қырмызы камзол. Қыл белін түрмемен қынай байлаған. Күміс ер-тұрман батқан күннің жалқын нұрына малынып жарқ-жұрқ етеді.

Шеге кеудесі аяққаптай, етжеңді балажігіт аюдай қорбаңдап, бүлкілдеп, далпылдап жүгіреді. Оның көзі мойыл, қара шашы желге үйіріліп ұшады.

Сырғаның дауысы құлаққа күміс қоңырау үніндей, есті, назды қылығымен табындырады. Оның түндей тұнық қара көзі, сабырлы сыр бүккен, сыңғырлаған күлкісі бар.`;
            
            document.getElementById('textInput').value = sampleText;
            showAlert('Үлгі мәтін жүктелді! Талдау батырмасын басыңыз.', 'success');
        }

        // Бет жүктелгенде
        window.addEventListener('DOMContentLoaded', function() {
            loadSampleText();
            
            // Smooth scroll
            document.querySelectorAll('a[href^="#"]').forEach(anchor => {
                anchor.addEventListener('click', function (e) {
                    e.preventDefault();
                    const target = document.querySelector(this.getAttribute('href'));
                    if (target) {
                        target.scrollIntoView({ behavior: 'smooth' });
                    }
                });
            });
        });
    </script>

    <!-- Bootstrap JS -->
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/js/bootstrap.bundle.min.js"></script>
</body>
</html>
