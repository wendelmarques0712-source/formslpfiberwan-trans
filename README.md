<style>
    @import url('https://fonts.googleapis.com/css2?family=Sora:wght@400;600;700&display=swap');

    :root {
        --fw-vermelho: #e70404;
        --fw-vermelho-hover: #c90303;
        --fw-preto-card: #0a0a0a;
        --fw-borda: #222222;
        --fw-branco: #ffffff;
        --fw-cinza-texto: #cccccc;
        --fw-input-bg: #f4f5f7;
        --font-main: 'Sora', sans-serif;
    }

    .tf-card {
        font-family: var(--font-main);
        background: var(--fw-preto-card);
        border: 1px solid var(--fw-borda);
        border-radius: 12px;
        padding: 50px 40px;
        box-shadow: 0 20px 40px rgba(0,0,0,0.6);
        max-width: 550px;
        margin: 0 auto;
        color: var(--fw-branco);
        text-align: left;
    }

    /* Cabeçalho do Form */
    .tf-sup-title {
        color: var(--fw-vermelho);
        font-size: 0.85rem;
        font-weight: 800;
        letter-spacing: 1px;
        text-transform: uppercase;
        margin-bottom: 10px;
    }

    .tf-main-title {
        font-size: 1.8rem;
        font-weight: 700;
        margin-bottom: 25px;
        line-height: 1.3;
    }

    /* Barras de Progresso */
    .tf-progress-container {
        display: flex;
        gap: 8px;
        margin-bottom: 35px;
    }

    .tf-progress-bar {
        height: 5px;
        flex: 1;
        background: #333333;
        border-radius: 3px;
        transition: background 0.4s ease;
    }

    .tf-progress-bar.active {
        background: var(--fw-vermelho);
    }

    /* Título da Etapa atual */
    .tf-step-title {
        font-size: 1.3rem;
        font-weight: 700;
        margin-bottom: 25px;
        color: var(--fw-branco);
    }

    /* Campos de Input */
    .tf-group {
        margin-bottom: 24px;
        position: relative;
    }

    .tf-group label {
        display: block;
        font-size: 1.05rem;
        font-weight: 600;
        margin-bottom: 10px;
        color: var(--fw-branco);
    }

    .tf-group input, .tf-group select {
        width: 100%;
        padding: 18px;
        background: var(--fw-input-bg);
        border: 2px solid transparent;
        border-radius: 8px;
        color: #000000;
        font-family: var(--font-main);
        font-size: 1.2rem;
        font-weight: 600; 
        outline: none;
        transition: all 0.3s ease;
        appearance: none;
    }

    .tf-group input::placeholder {
        font-weight: 400;
        color: #7a7a7a;
        font-size: 1.05rem;
    }

    .tf-group input:focus, .tf-group select:focus {
        border-color: var(--fw-vermelho);
        background: var(--fw-branco);
    }

    .tf-group input.error-input, .tf-group select.error-input {
        border-color: var(--fw-vermelho);
        background: #fff5f5;
    }

    /* Ocultar etapas */
    .tf-step {
        display: none;
        animation: fadeIn 0.4s ease;
    }

    .tf-step.active {
        display: block;
    }

    @keyframes fadeIn {
        from { opacity: 0; transform: translateY(10px); }
        to { opacity: 1; transform: translateY(0); }
    }

    /* Botões */
    .tf-footer {
        display: flex;
        gap: 15px;
        margin-top: 15px; /* Ajustado para compensar a caixa de erro */
    }

    .btn-tf {
        flex: 1;
        padding: 20px 16px;
        font-size: 1.2rem;
        font-weight: 700;
        border-radius: 8px;
        cursor: pointer;
        font-family: var(--font-main);
        transition: all 0.3s ease;
        text-align: center;
        border: none;
    }

    .btn-primary {
        background: var(--fw-vermelho);
        color: var(--fw-branco);
    }

    .btn-primary:hover {
        background: var(--fw-vermelho-hover);
        transform: translateY(-2px);
    }

    .btn-secondary {
        background: #1a1a1a;
        color: var(--fw-cinza-texto);
        border: 1px solid #333333;
    }

    .btn-secondary:hover {
        background: #252525;
        color: var(--fw-branco);
    }
    
    /* Mensagens de Erro - NOVA CAIXA COM ROLAGEM */
    .tf-error-msg {
        color: var(--fw-vermelho);
        font-size: 0.85rem;
        margin-top: -5px;
        margin-bottom: 15px;
        display: none;
        font-weight: 600;
        background: rgba(231, 4, 4, 0.1);
        padding: 10px 15px;
        border-radius: 6px;
        border-left: 3px solid var(--fw-vermelho);
        max-height: 60px; /* Impede que o formulário cresça */
        overflow-y: auto; /* Adiciona a barra de rolagem */
    }

    /* Customização da barra de rolagem do erro */
    .tf-error-msg::-webkit-scrollbar {
        width: 6px;
    }
    .tf-error-msg::-webkit-scrollbar-thumb {
        background: var(--fw-vermelho);
        border-radius: 4px;
    }

    /* ===== AJUSTES PARA MOBILE ===== */
    @media (max-width: 768px) {
        .tf-card {
            padding: 30px 20px;
            max-width: 100%;
        }
        .tf-main-title { font-size: 1.5rem; }
        .tf-step-title { font-size: 1.2rem; }
        .tf-group label { font-size: 1rem; }
        .tf-group input, .tf-group select { font-size: 1.1rem; padding: 15px; }
        .btn-tf { padding: 16px; font-size: 1.1rem; }
        .tf-footer { flex-direction: column; }
        .btn-secondary { order: 2; }
        .btn-primary { order: 1; }
    }
</style>

<div class="tf-card" id="formulario">
    <div class="tf-sup-title">Solicitação de Orçamento</div>
    <div class="tf-main-title">Fale com um especialista FiberWan</div>

    <div class="tf-progress-container">
        <div class="tf-progress-bar active" id="bar-1"></div>
        <div class="tf-progress-bar" id="bar-2"></div>
    </div>

    <form id="tf-lead-form" action="/seu-link-de-obrigado" method="POST">
        
        <div class="tf-step active" id="step-1">
            <div class="tf-step-title">Dados de contato</div>
            
            <div class="tf-group">
                <label for="tf-nome">Nome Completo:</label>
                <input type="text" id="tf-nome" name="nome" placeholder="Ex: João da Silva" required>
            </div>
            
            <div class="tf-group">
                <label for="tf-email">E-mail Profissional:</label>
                <input type="email" id="tf-email" name="email" placeholder="joao@gmail.com" required>
            </div>
            
            <div class="tf-group">
                <label for="tf-telefone">Telefone / WhatsApp:</label>
                <input type="tel" id="tf-telefone" name="telefone" placeholder="11 90000-0000" maxlength="15" required>
            </div>

            <div class="tf-error-msg" id="error-step-1"></div>

            <div class="tf-footer">
                <button type="button" class="btn-tf btn-primary" onclick="nextStep()">Continuar</button>
            </div>
        </div>

        <div class="tf-step" id="step-2">
            <div class="tf-step-title">Dados da empresa</div>

            <div class="tf-group">
                <label for="tf-empresa">Nome da Empresa:</label>
                <input type="text" id="tf-empresa" name="empresa" placeholder="Sua empresa" required>
            </div>

            <div class="tf-group">
                <label for="tf-segmento">Segmento de atuação:</label>
                <select id="tf-segmento" name="segmento" required>
                    <option value="" disabled selected>Selecione um segmento</option>
                    <option>Provedor de internet / ISP</option>
                    <option>Integrador de redes ou segurança eletrônica</option>
                    <option>Empresa de telecomunicações</option>
                    <option>Distribuidor de tecnologia/automação</option>
                    <option>Instalador autônomo / técnico</option>
                    <option>Revenda de equipamentos de rede</option>
                    <option>Empresa de outro segmento</option>
                    <option>Não tenho uma empresa</option>
                </select>
            </div>

            <div class="tf-error-msg" id="error-step-2"></div>

            <div class="tf-footer">
                <button type="button" class="btn-tf btn-secondary" onclick="prevStep()">Voltar</button>
                <button type="submit" class="btn-tf btn-primary">Quero eliminar instabilidades!</button>
            </div>
        </div>

    </form>
</div>

<script>
    // --- FUNÇÕES DE VALIDAÇÃO SIMPLIFICADAS ---
    function validateName(name) {
        // Exige apenas que haja pelo menos uma palavra seguida de um espaço e outra palavra
        return name.trim().split(/\s+/).length >= 2;
    }

    function validateEmail(email) {
        // Regex universal que aceita genéricos (@gmail, @hotmail, etc)
        const regex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
        return regex.test(email.trim());
    }

    function validatePhone(phone) {
        // Conta apenas se tem exatamente 11 dígitos, ignorando traços e espaços
        let numbers = phone.replace(/\D/g, '');
        return numbers.length === 11;
    }

    function clearErrors(stepId) {
        const step = document.getElementById(stepId);
        const inputs = step.querySelectorAll('input, select');
        inputs.forEach(input => input.classList.remove('error-input'));
    }

    // --- LÓGICA DE AVANÇO ETAPA 1 ---
    function nextStep() {
        clearErrors('step-1');
        const inputNome = document.getElementById('tf-nome');
        const inputEmail = document.getElementById('tf-email');
        const inputTelefone = document.getElementById('tf-telefone');
        const errorElement = document.getElementById('error-step-1');
        
        let isValid = true;
        let errorMessages = [];

        // 1. Validação do Nome
        if (!validateName(inputNome.value)) {
            inputNome.classList.add('error-input');
            errorMessages.push("• Insira o seu nome e sobrenome.");
            isValid = false;
        }

        // 2. Validação do E-mail
        if (!validateEmail(inputEmail.value)) {
            inputEmail.classList.add('error-input');
            errorMessages.push("• Insira um e-mail válido.");
            isValid = false;
        }

        // 3. Validação do Telefone
        if (!validatePhone(inputTelefone.value)) {
            inputTelefone.classList.add('error-input');
            errorMessages.push("• Insira o telefone com DDD (11 dígitos).");
            isValid = false;
        }

        if (isValid) {
            errorElement.style.display = 'none';
            document.getElementById('step-1').classList.remove('active');
            document.getElementById('step-2').classList.add('active');
            document.getElementById('bar-2').classList.add('active');
        } else {
            errorElement.innerHTML = errorMessages.join("<br>");
            errorElement.style.display = 'block';
        }
    }

    // --- LÓGICA DE VOLTAR ---
    function prevStep() {
        document.getElementById('step-2').classList.remove('active');
        document.getElementById('step-1').classList.add('active');
        document.getElementById('bar-2').classList.remove('active');
    }

    // --- LÓGICA DE ENVIO FINAL ETAPA 2 ---
    const form = document.getElementById('tf-lead-form');
    form.addEventListener('submit', function(e) {
        clearErrors('step-2');
        const inputEmpresa = document.getElementById('tf-empresa');
        const selectSegmento = document.getElementById('tf-segmento');
        const errorElement = document.getElementById('error-step-2');
        
        let isValid = true;
        let errorMessages = [];

        if (inputEmpresa.value.trim().length < 2) {
            inputEmpresa.classList.add('error-input');
            errorMessages.push("• Preencha o nome da sua empresa.");
            isValid = false;
        }

        if (!selectSegmento.value) {
            selectSegmento.classList.add('error-input');
            errorMessages.push("• Selecione o seu segmento de atuação.");
            isValid = false;
        }

        if (!isValid) {
            e.preventDefault(); 
            errorElement.innerHTML = errorMessages.join("<br>");
            errorElement.style.display = 'block';
        }
    });

    // --- MÁSCARA DO TELEFONE ---
    const inputPhoneMask = document.getElementById('tf-telefone');
    inputPhoneMask.addEventListener('input', function (e) {
        let value = e.target.value;
        let numbers = "";
        
        for (let i = 0; i < value.length; i++) {
            if (value[i] >= '0' && value[i] <= '9') {
                numbers += value[i];
            }
        }

        if (numbers.length > 11) numbers = numbers.substring(0, 11);

        let finalValue = "";
        if (numbers.length === 0) finalValue = "";
        else if (numbers.length <= 2) finalValue = numbers;
        else if (numbers.length <= 6) finalValue = numbers.substring(0, 2) + " " + numbers.substring(2);
        else if (numbers.length <= 10) finalValue = numbers.substring(0, 2) + " " + numbers.substring(2, 6) + "-" + numbers.substring(6);
        else finalValue = numbers.substring(0, 2) + " " + numbers.substring(2, 7) + "-" + numbers.substring(7);
        
        e.target.value = finalValue;
    });
</script>
