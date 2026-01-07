# CathPCI-Coding[pci-dictionary-search (2).html](https://github.com/user-attachments/files/24462020/pci-dictionary-search.2.html)
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PCI Registry Data Dictionary v5.0</title>
    <link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;600;700&family=Libre+Baskerville:wght@400;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary: #1a4d6d;
            --secondary: #2d7fa6;
            --accent: #00a8cc;
            --highlight: #ffa726;
            --bg-main: #f8f9fa;
            --bg-card: #ffffff;
            --text-primary: #1a1a1a;
            --text-secondary: #5a6c7d;
            --border: #d4dfe8;
            --shadow: rgba(26, 77, 109, 0.08);
            --success: #4caf50;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'JetBrains Mono', monospace;
            background: linear-gradient(135deg, #f8f9fa 0%, #e8eef3 100%);
            color: var(--text-primary);
            line-height: 1.6;
            min-height: 100vh;
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 2rem;
        }

        header {
            background: linear-gradient(135deg, var(--primary) 0%, var(--secondary) 100%);
            color: white;
            padding: 2.5rem 2rem;
            border-radius: 16px;
            margin-bottom: 2rem;
            box-shadow: 0 8px 32px var(--shadow);
            position: relative;
            overflow: hidden;
        }

        header::before {
            content: '';
            position: absolute;
            top: 0;
            right: 0;
            width: 300px;
            height: 300px;
            background: radial-gradient(circle, rgba(255,255,255,0.1) 0%, transparent 70%);
            border-radius: 50%;
            transform: translate(30%, -30%);
        }

        h1 {
            font-family: 'Libre Baskerville', serif;
            font-size: 2.5rem;
            font-weight: 700;
            margin-bottom: 0.5rem;
            position: relative;
            z-index: 1;
        }

        .version {
            font-size: 0.95rem;
            opacity: 0.9;
            font-weight: 400;
            letter-spacing: 0.5px;
        }

        .search-container {
            background: var(--bg-card);
            padding: 2rem;
            border-radius: 12px;
            box-shadow: 0 4px 16px var(--shadow);
            margin-bottom: 2rem;
            border: 1px solid var(--border);
        }

        .search-group {
            display: grid;
            grid-template-columns: 1fr auto;
            gap: 1rem;
            margin-bottom: 1rem;
        }

        .input-wrapper {
            position: relative;
        }

        input[type="text"] {
            width: 100%;
            padding: 1rem 1.25rem;
            border: 2px solid var(--border);
            border-radius: 8px;
            font-family: 'JetBrains Mono', monospace;
            font-size: 1rem;
            transition: all 0.3s ease;
            background: var(--bg-main);
        }

        input[type="text"]:focus {
            outline: none;
            border-color: var(--accent);
            box-shadow: 0 0 0 3px rgba(0, 168, 204, 0.1);
        }

        button {
            padding: 1rem 2rem;
            background: var(--accent);
            color: white;
            border: none;
            border-radius: 8px;
            font-family: 'JetBrains Mono', monospace;
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            white-space: nowrap;
        }

        button:hover {
            background: var(--secondary);
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(0, 168, 204, 0.3);
        }

        button:active {
            transform: translateY(0);
        }

        .stats {
            display: flex;
            gap: 2rem;
            justify-content: space-between;
            padding: 1rem 0;
            border-top: 1px solid var(--border);
            margin-top: 1rem;
            font-size: 0.9rem;
            color: var(--text-secondary);
        }

        .stat-item {
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        .stat-value {
            font-weight: 700;
            color: var(--accent);
            font-size: 1.1rem;
        }

        .results-container {
            display: grid;
            gap: 1.5rem;
        }

        .result-card {
            background: var(--bg-card);
            border-radius: 12px;
            padding: 1.75rem;
            box-shadow: 0 2px 8px var(--shadow);
            border-left: 4px solid var(--accent);
            transition: all 0.3s ease;
            animation: slideIn 0.4s ease;
        }

        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateY(20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .result-card:hover {
            box-shadow: 0 8px 24px var(--shadow);
            transform: translateY(-4px);
            border-left-color: var(--highlight);
        }

        .element-header {
            display: flex;
            justify-content: space-between;
            align-items: start;
            margin-bottom: 1.25rem;
            gap: 1rem;
        }

        .element-ref {
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
            padding: 0.5rem 1rem;
            border-radius: 6px;
            font-weight: 700;
            font-size: 1.1rem;
            min-width: 100px;
            text-align: center;
            box-shadow: 0 2px 8px rgba(26, 77, 109, 0.2);
        }

        .element-name {
            font-family: 'Libre Baskerville', serif;
            font-size: 1.4rem;
            font-weight: 700;
            color: var(--primary);
            flex: 1;
            line-height: 1.3;
        }

        .field-group {
            margin-bottom: 1.25rem;
        }

        .field-group:last-child {
            margin-bottom: 0;
        }

        .field-label {
            font-weight: 700;
            color: var(--secondary);
            text-transform: uppercase;
            font-size: 0.8rem;
            letter-spacing: 0.5px;
            margin-bottom: 0.5rem;
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        .field-label::before {
            content: '';
            width: 4px;
            height: 4px;
            background: var(--accent);
            border-radius: 50%;
        }

        .field-content {
            color: var(--text-primary);
            padding: 0.75rem;
            background: var(--bg-main);
            border-radius: 6px;
            white-space: pre-wrap;
            line-height: 1.7;
            font-size: 0.95rem;
        }

        .empty-state {
            text-align: center;
            padding: 4rem 2rem;
            color: var(--text-secondary);
        }

        .empty-state-icon {
            font-size: 4rem;
            margin-bottom: 1rem;
            opacity: 0.3;
        }

        .no-results {
            background: var(--bg-card);
            border-radius: 12px;
            padding: 3rem;
            text-align: center;
            box-shadow: 0 2px 8px var(--shadow);
        }

        .no-results-icon {
            font-size: 3rem;
            margin-bottom: 1rem;
        }

        .loading {
            text-align: center;
            padding: 2rem;
            color: var(--text-secondary);
            font-weight: 600;
        }

        .highlight {
            background: linear-gradient(120deg, rgba(255, 167, 38, 0.2) 0%, rgba(255, 167, 38, 0.1) 100%);
            padding: 0.15rem 0.3rem;
            border-radius: 3px;
            font-weight: 600;
        }

        @media (max-width: 768px) {
            .container {
                padding: 1rem;
            }

            h1 {
                font-size: 1.8rem;
            }

            .search-group {
                grid-template-columns: 1fr;
            }

            .stats {
                flex-direction: column;
                gap: 0.75rem;
            }

            .element-header {
                flex-direction: column;
            }

            .element-ref {
                align-self: flex-start;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>PCI Registry Data Dictionary</h1>
            <div class="version">Version 5.0 | Release Date: January 5, 2026</div>
        </header>

        <div class="search-container">
            <div class="search-group">
                <div class="input-wrapper">
                    <input 
                        type="text" 
                        id="searchInput" 
                        placeholder="Search by keyword, element name, or element reference number (e.g., '2000' or 'patient name')..."
                        autofocus
                    >
                </div>
                <button onclick="performSearch()">Search</button>
            </div>
            <div class="stats">
                <div class="stat-item">
                    <span>Total Elements:</span>
                    <span class="stat-value" id="totalElements">996</span>
                </div>
                <div class="stat-item">
                    <span>Results Found:</span>
                    <span class="stat-value" id="resultsCount">0</span>
                </div>
            </div>
        </div>

        <div id="resultsContainer" class="results-container">
            <div class="empty-state">
                <div class="empty-state-icon">🔍</div>
                <h2>Search the PCI Data Dictionary</h2>
                <p>Enter a keyword, element name, or element reference number to find registry specifications.</p>
            </div>
        </div>
    </div>

    <script src="https://cdnjs.cloudflare.com/ajax/libs/PapaParse/5.4.1/papaparse.min.js"></script>
    <script>
        let dictionaryData = [];

        // Load CSV data
        async function loadData() {
            try {
                const response = await fetch('/mnt/user-data/uploads/pci_v5-0_datadictionaryfullspecifications_rtd_01052026.csv');
                const csvText = await response.text();
                
                Papa.parse(csvText, {
                    header: true,
                    skipEmptyLines: true,
                    complete: function(results) {
                        dictionaryData = results.data;
                        document.getElementById('totalElements').textContent = dictionaryData.length;
                    }
                });
            } catch (error) {
                console.error('Error loading data:', error);
                document.getElementById('resultsContainer').innerHTML = `
                    <div class="no-results">
                        <div class="no-results-icon">⚠️</div>
                        <h3>Error loading data</h3>
                        <p>Unable to load the data dictionary file.</p>
                    </div>
                `;
            }
        }

        function highlightText(text, searchTerm) {
            if (!searchTerm || !text) return text || '';
            const regex = new RegExp(`(${searchTerm.replace(/[.*+?^${}()|[\]\\]/g, '\\$&')})`, 'gi');
            return text.replace(regex, '<span class="highlight">$1</span>');
        }

        function performSearch() {
            const searchTerm = document.getElementById('searchInput').value.trim().toLowerCase();
            const resultsContainer = document.getElementById('resultsContainer');
            
            if (!searchTerm) {
                resultsContainer.innerHTML = `
                    <div class="empty-state">
                        <div class="empty-state-icon">🔍</div>
                        <h2>Search the PCI Data Dictionary</h2>
                        <p>Enter a keyword, element name, or element reference number to find registry specifications.</p>
                    </div>
                `;
                document.getElementById('resultsCount').textContent = '0';
                return;
            }

            const results = dictionaryData.filter(item => {
                return (
                    (item['Element Reference'] && item['Element Reference'].toLowerCase().includes(searchTerm)) ||
                    (item['Name'] && item['Name'].toLowerCase().includes(searchTerm)) ||
                    (item['Coding Instructions'] && item['Coding Instructions'].toLowerCase().includes(searchTerm)) ||
                    (item['Target Value'] && item['Target Value'].toLowerCase().includes(searchTerm)) ||
                    (item['Supporting Definition'] && item['Supporting Definition'].toLowerCase().includes(searchTerm))
                );
            });

            document.getElementById('resultsCount').textContent = results.length;

            if (results.length === 0) {
                resultsContainer.innerHTML = `
                    <div class="no-results">
                        <div class="no-results-icon">🔍</div>
                        <h3>No results found</h3>
                        <p>Try different keywords or check the element reference number.</p>
                    </div>
                `;
                return;
            }

            resultsContainer.innerHTML = results.map((item, index) => `
                <div class="result-card" style="animation-delay: ${index * 0.05}s">
                    <div class="element-header">
                        <div class="element-ref">${highlightText(item['Element Reference'], searchTerm)}</div>
                        <div class="element-name">${highlightText(item['Name'], searchTerm)}</div>
                    </div>
                    
                    ${item['Coding Instructions'] ? `
                        <div class="field-group">
                            <div class="field-label">Coding Instructions</div>
                            <div class="field-content">${highlightText(item['Coding Instructions'], searchTerm)}</div>
                        </div>
                    ` : ''}
                    
                    ${item['Target Value'] ? `
                        <div class="field-group">
                            <div class="field-label">Target Value</div>
                            <div class="field-content">${highlightText(item['Target Value'], searchTerm)}</div>
                        </div>
                    ` : ''}
                    
                    ${item['Supporting Definition'] ? `
                        <div class="field-group">
                            <div class="field-label">Supporting Definition</div>
                            <div class="field-content">${highlightText(item['Supporting Definition'], searchTerm)}</div>
                        </div>
                    ` : ''}
                </div>
            `).join('');
        }

        // Enable search on Enter key
        document.addEventListener('DOMContentLoaded', function() {
            loadData();
            
            document.getElementById('searchInput').addEventListener('keypress', function(e) {
                if (e.key === 'Enter') {
                    performSearch();
                }
            });

            // Real-time search as user types (with debounce)
            let debounceTimer;
            document.getElementById('searchInput').addEventListener('input', function() {
                clearTimeout(debounceTimer);
                debounceTimer = setTimeout(performSearch, 300);
            });
        });
    </script>
</body>
</html>
