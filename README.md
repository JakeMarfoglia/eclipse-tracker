# eclipse-tracker
Top 3 To-Do's Tracker For Work/Life Balance
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>My Notion Widget</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <style>
    /* Optional: basic reset so it looks good in the embed */
    html, body {
      margin: 0;
      padding: 0;
      background: transparent;
      font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
    }
  </style>
</head>
<body>
  <!-- Your widget HTML goes here -->
  <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DNA Helix Balance Widget</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            background: #000000;
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
            display: flex;
            align-items: center;
            justify-content: center;
            min-height: 100vh;
            padding: 16px;
        }
        
        .widget {
            width: 100%;
            max-width: 440px;
            background: linear-gradient(145deg, #0a0a12 0%, #16162a 100%);
            border-radius: 24px;
            padding: 28px;
            border: 1px solid rgba(255, 255, 255, 0.06);
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.5);
        }
        
        .helix-container {
            position: relative;
            width: 100%;
            height: 200px;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 24px;
            background: rgba(0, 0, 0, 0.2);
            border-radius: 16px;
            overflow: hidden;
        }
        
        .helix-canvas {
            width: 100%;
            height: 100%;
        }
        
        .status-bar {
            text-align: center;
            margin-bottom: 24px;
        }
        
        .alignment-percentage {
            font-size: 42px;
            font-weight: 800;
            background: linear-gradient(135deg, #00d4ff, #0099ff);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 10px;
            line-height: 1;
            letter-spacing: -1px;
        }
        
        .status {
            font-size: 13px;
            font-weight: 600;
            letter-spacing: 0.5px;
            padding: 10px 20px;
            border-radius: 10px;
            background: rgba(255, 255, 255, 0.04);
            display: inline-block;
            color: rgba(255, 255, 255, 0.7);
        }
        
        .status.perfect {
            background: linear-gradient(90deg, 
                rgba(0, 212, 255, 0.12),
                rgba(0, 212, 255, 0.2),
                rgba(0, 212, 255, 0.12)
            );
            background-size: 200% 100%;
            color: #00d4ff;
            animation: shimmerBackground 2.5s ease-in-out infinite;
        }
        
        @keyframes shimmerBackground {
            0%, 100% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
        }
        
        .tasks-container {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 14px;
        }
        
        .task-section {
            background: rgba(255, 255, 255, 0.02);
            border-radius: 14px;
            padding: 18px;
            border: 1px solid rgba(255, 255, 255, 0.06);
            min-width: 0;
        }
        
        .task-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 14px;
            padding-bottom: 12px;
            border-bottom: 1px solid rgba(255, 255, 255, 0.08);
        }
        
        .task-title {
            font-size: 12px;
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 1px;
            color: rgba(255, 255, 255, 0.85);
        }
        
        .task-count {
            font-size: 11px;
            padding: 4px 10px;
            background: rgba(255, 255, 255, 0.08);
            border-radius: 10px;
            font-weight: 700;
            color: rgba(255, 255, 255, 0.7);
        }
        
        .task-item {
            display: flex;
            align-items: center;
            gap: 10px;
            margin-bottom: 10px;
            padding: 10px;
            background: rgba(0, 0, 0, 0.25);
            border-radius: 8px;
            transition: all 0.2s ease;
            min-width: 0;
        }
        
        .task-item:last-child {
            margin-bottom: 0;
        }
        
        .task-item:hover {
            background: rgba(0, 0, 0, 0.35);
        }
        
        .task-item.completed {
            opacity: 0.45;
        }
        
        .task-item.completed input[type="text"] {
            text-decoration: line-through;
        }
        
        input[type="checkbox"] {
            width: 18px;
            height: 18px;
            cursor: pointer;
            accent-color: #0099ff;
            flex-shrink: 0;
        }
        
        input[type="text"] {
            flex: 1;
            background: transparent;
            border: none;
            color: rgba(255, 255, 255, 0.9);
            font-size: 13px;
            outline: none;
            font-family: inherit;
            padding: 2px 0;
            min-width: 0;
        }
        
        input[type="text"]::placeholder {
            color: rgba(255, 255, 255, 0.25);
        }
        
        @media (max-width: 480px) {
            .widget {
                padding: 24px;
            }
            
            .tasks-container {
                grid-template-columns: 1fr;
            }
            
            .helix-container {
                height: 180px;
            }
        }
    </style>
</head>
<body>
    <div class="widget">
        <div class="helix-container">
            <canvas id="helixCanvas" class="helix-canvas"></canvas>
        </div>
        
        <div class="status-bar">
            <div class="alignment-percentage" id="alignment">100%</div>
            <div class="status" id="status">Perfect Helix ✨</div>
        </div>
        
        <div class="tasks-container">
            <div class="task-section">
                <div class="task-header">
                    <div class="task-title">⚙️ Work</div>
                    <div class="task-count" id="workCount">0/3</div>
                </div>
                <div id="workTasks"></div>
            </div>
            
            <div class="task-section">
                <div class="task-header">
                    <div class="task-title">🌿 Life</div>
                    <div class="task-count" id="lifeCount">0/3</div>
                </div>
                <div id="lifeTasks"></div>
            </div>
        </div>
    </div>

    <script>
        const canvas = document.getElementById('helixCanvas');
        const ctx = canvas.getContext('2d');
        const workTasksContainer = document.getElementById('workTasks');
        const lifeTasksContainer = document.getElementById('lifeTasks');
        const workCount = document.getElementById('workCount');
        const lifeCount = document.getElementById('lifeCount');
        const status = document.getElementById('status');
        const alignment = document.getElementById('alignment');
        
        let workTasks = [
            { text: '', completed: false },
            { text: '', completed: false },
            { text: '', completed: false }
        ];
        
        let lifeTasks = [
            { text: '', completed: false },
            { text: '', completed: false },
            { text: '', completed: false }
        ];
        
        let animationFrame = 0;
        
        function resizeCanvas() {
            const rect = canvas.getBoundingClientRect();
            canvas.width = rect.width * window.devicePixelRatio;
            canvas.height = rect.height * window.devicePixelRatio;
            ctx.scale(window.devicePixelRatio, window.devicePixelRatio);
        }
        
        function drawHelix(workPercent, lifePercent) {
            const rect = canvas.getBoundingClientRect();
            const w = rect.width;
            const h = rect.height;
            
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            
            const centerY = h / 2;
            const amplitude = 40;
            const frequency = 0.03;
            const numPoints = 100;
            
            // Calculate imbalance (0 = perfect, 1 = max imbalance)
            const imbalance = Math.abs(workPercent - lifePercent);
            
            animationFrame += 0.02;
            
            // Draw Work strand (top strand - BLUE)
            ctx.shadowBlur = 0;
            ctx.shadowColor = 'transparent';
            ctx.beginPath();
            ctx.strokeStyle = 'blue';
            ctx.lineWidth = 5;
            
            for (let i = 0; i < numPoints; i++) {
                const x = (i / numPoints) * w;
                const distortion = (workPercent - 0.5) * 60;
                const y = centerY + Math.sin(i * frequency + animationFrame) * (amplitude + distortion);
                
                if (i === 0) ctx.moveTo(x, y);
                else ctx.lineTo(x, y);
            }
            ctx.stroke();
            
            // Draw Life strand (bottom strand - RED)
            ctx.shadowBlur = 0;
            ctx.shadowColor = 'transparent';
            ctx.beginPath();
            ctx.strokeStyle = 'red';
            ctx.lineWidth = 5;
            
            for (let i = 0; i < numPoints; i++) {
                const x = (i / numPoints) * w;
                // More distortion when work is higher
                const distortion = (workPercent - 0.5) * 60;
                const y = centerY + Math.sin(i * frequency + animationFrame) * (amplitude + distortion);
                
                if (i === 0) ctx.moveTo(x, y);
                else ctx.lineTo(x, y);
            }
            ctx.stroke();
            
            // Draw Life strand (bottom strand - magenta)
            ctx.beginPath();
            ctx.strokeStyle = `rgba(255, 0, 128, ${0.5 + imbalance * 0.5})`;
            ctx.lineWidth = 4;
            
            for (let i = 0; i < numPoints; i++) {
                const x = (i / numPoints) * w;
                // More distortion when life is higher
                const distortion = (lifePercent - 0.5) * 60;
                const y = centerY - Math.sin(i * frequency + animationFrame) * (amplitude + distortion);
                
                if (i === 0) ctx.moveTo(x, y);
                else ctx.lineTo(x, y);
            }
            ctx.stroke();
            
            // Draw connecting rungs when balanced
            if (imbalance < 0.4) {
                ctx.strokeStyle = `rgba(255, 255, 255, ${0.3 * (1 - imbalance / 0.4)})`;
                ctx.lineWidth = 2;
                ctx.shadowBlur = 10;
                ctx.shadowColor = 'rgba(255, 255, 255, 0.5)';
                
                for (let i = 0; i < numPoints; i += 8) {
                    const x = (i / numPoints) * w;
                    const y1 = centerY + Math.sin(i * frequency + animationFrame) * amplitude;
                    const y2 = centerY - Math.sin(i * frequency + animationFrame) * amplitude;
                    
                    ctx.beginPath();
                    ctx.moveTo(x, y1);
                    ctx.lineTo(x, y2);
                    ctx.stroke();
                }
            }
            
            // Reset shadow
            ctx.shadowBlur = 0;
            
            requestAnimationFrame(animate);
        }
        
        function createTaskItem(task, index, isWork) {
            const div = document.createElement('div');
            div.className = 'task-item' + (task.completed ? ' completed' : '');
            
            const checkbox = document.createElement('input');
            checkbox.type = 'checkbox';
            checkbox.checked = task.completed;
            checkbox.addEventListener('change', (e) => {
                task.completed = e.target.checked;
                updateBalance();
                renderTasks();
            });
            
            const input = document.createElement('input');
            input.type = 'text';
            input.placeholder = `Task ${index + 1}...`;
            input.value = task.text;
            input.addEventListener('input', (e) => {
                task.text = e.target.value;
            });
            
            div.appendChild(checkbox);
            div.appendChild(input);
            
            return div;
        }
        
        function renderTasks() {
            workTasksContainer.innerHTML = '';
            lifeTasksContainer.innerHTML = '';
            
            workTasks.forEach((task, i) => {
                workTasksContainer.appendChild(createTaskItem(task, i, true));
            });
            
            lifeTasks.forEach((task, i) => {
                lifeTasksContainer.appendChild(createTaskItem(task, i, false));
            });
        }
        
        function updateBalance() {
            const workCompleted = workTasks.filter(t => t.completed).length;
            const lifeCompleted = lifeTasks.filter(t => t.completed).length;
            
            workCount.textContent = `${workCompleted}/3`;
            lifeCount.textContent = `${lifeCompleted}/3`;
            
            const workPercent = workCompleted / 3;
            const lifePercent = lifeCompleted / 3;
            const difference = Math.abs(workPercent - lifePercent) * 100;
            const alignmentPercent = Math.max(0, 100 - difference);
            
            alignment.textContent = Math.round(alignmentPercent) + '%';
            
            if (difference <= 20) {
                status.textContent = 'Perfect Helix ✨';
                status.className = 'status perfect';
            } else if (difference <= 40) {
                status.textContent = 'Nearly Aligned 🧬';
                status.className = 'status';
            } else if (difference <= 60) {
                status.textContent = 'Seeking Balance 🔬';
                status.className = 'status';
            } else {
                if (workPercent > lifePercent) {
                    status.textContent = 'Work Heavy ⚖️';
                } else {
                    status.textContent = 'Life Heavy ⚖️';
                }
                status.className = 'status';
            }
        }
        
        let currentWorkPercent = 0;
        let currentLifePercent = 0;
        
        function animate() {
            drawHelix(currentWorkPercent, currentLifePercent);
        }
        
        function updateBalance() {
            const workCompleted = workTasks.filter(t => t.completed).length;
            const lifeCompleted = lifeTasks.filter(t => t.completed).length;
            
            workCount.textContent = `${workCompleted}/3`;
            lifeCount.textContent = `${lifeCompleted}/3`;
            
            currentWorkPercent = workCompleted / 3;
            currentLifePercent = lifeCompleted / 3;
            
            const difference = Math.abs(currentWorkPercent - currentLifePercent) * 100;
            const alignmentPercent = Math.max(0, 100 - difference);
            
            alignment.textContent = Math.round(alignmentPercent) + '%';
            
            if (difference <= 20) {
                status.textContent = 'Perfect Helix ✨';
                status.className = 'status perfect';
            } else if (difference <= 40) {
                status.textContent = 'Nearly Aligned 🧬';
                status.className = 'status';
            } else if (difference <= 60) {
                status.textContent = 'Seeking Balance 🔬';
                status.className = 'status';
            } else {
                if (currentWorkPercent > currentLifePercent) {
                    status.textContent = 'Work Heavy ⚖️';
                } else {
                    status.textContent = 'Life Heavy ⚖️';
                }
                status.className = 'status';
            }
        }
        
        window.addEventListener('resize', resizeCanvas);
        resizeCanvas();
        renderTasks();
        updateBalance();
        animate();
    </script>
</body>
</html>
  <div id="eclipsewidget">
    <!-- ... -->
  </div>

  <!-- If you have JS, include it here -->
  <script>
    // your widget logic
  </script>
</body>
</html>
