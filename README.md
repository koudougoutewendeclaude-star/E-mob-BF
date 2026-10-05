# E-mob-BF
VENTE DE PARCELLE ET ACHAT 
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>E'Mob BF - Vente et Achat de Parcelles au Burkina Faso</title>
    <style>
        :root {
            --primary: #2e7d32;
            --secondary: #fbc02d;
            --dark: #1b5e20;
            --light: #f1f8e9;
            --gray: #f5f5f5;
        }
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: var(--light);
            margin: 0;
            padding: 0;
            color: #333;
        }
        header {
            background-color: var(--primary);
            color: white;
            padding: 20px;
            text-align: center;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
        }
        header h1 {
            margin: 0;
            font-size: 24px;
        }
        header p {
            margin: 5px 0 0 0;
            font-size: 14px;
            color: var(--secondary);
        }
        .container {
            max-width: 600px;
            margin: 20px auto;
            background: white;
            padding: 20px;
            border-radius: 12px;
            box-shadow: 0 4px 12px rgba(0,0,0,0.05);
        }
        .roles-selector {
            display: flex;
            gap: 10px;
            margin-bottom: 20px;
        }
        .role-btn {
            flex: 1;
            padding: 12px;
            border: 2px solid var(--primary);
            background: white;
            color: var(--primary);
            font-weight: bold;
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.3s;
            text-align: center;
        }
        .role-btn.active {
            background: var(--primary);
            color: white;
        }
        .form-section {
            display: none;
        }
        .form-section.active {
            display: block;
        }
        .form-group {
            margin-bottom: 15px;
        }
        label {
            display: block;
            margin-bottom: 5px;
            font-weight: 600;
            font-size: 14px;
        }
        input, select, textarea {
            width: 100%;
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 6px;
            box-sizing: border-box;
        }
        .btn-submit {
            background-color: var(--primary);
            color: white;
            border: none;
            padding: 12px;
            width: 100%;
            border-radius: 6px;
            font-size: 16px;
            font-weight: bold;
            cursor: pointer;
            margin-top: 10px;
        }
        .btn-submit:hover {
            background-color: var(--dark);
        }
        .contract-box {
            background: #fff8e1;
            border: 1px solid #ffe082;
            padding: 10px;
            font-size: 12px;
            border-radius: 6px;
            margin-bottom: 15px;
            max-height: 100px;
            overflow-y: auto;
        }
    </style>
</head>
<body>

    <header>
        <h1>🏡 E'Mob BF</h1>
        <p>Acquérez votre parcelle au Burkina Faso en toute sécurité (Intérieur & Diaspora)</p>
    </header>

    <div class="container">
        <div class="roles-selector">
            <button class="role-btn active" onclick="switchRole('acheteur')">Acheteur</button>
            <button class="role-btn" onclick="switchRole('vendeur')">Vendeur</button>
            <button class="role-btn" onclick="switchRole('visiteur')">Visiteur</button>
        </div>

        <!-- Section Acheteur -->
        <div id="acheteur" class="form-section active">
            <h2>Espace Acheteur</h2>
            <form onsubmit="handleAcheteur(event)">
                <div class="form-group">
                    <label>Nom et Prénom</label>
                    <input type="text" required placeholder="Ex: Koudougou Tewende Claude">
                </div>
                <div class="form-group">
                    <label>Numéro de Téléphone</label>
                    <input type="tel" required placeholder="Ex: +226 ...">
                </div>
                <div class="form-group">
                    <label>Numéro CNIB ou Passeport</label>
                    <input type="text" required placeholder="N° de pièce d'identité">
                </div>
                <div class="form-group">
                    <label>Êtes-vous un démarcheur ?</label>
                    <select id="isDemarcheur" onchange="toggleDemarcheurFields()">
                        <option value="non">Non</option>
                        <option value="oui">Oui</option>
                    </select>
                </div>
                
                <div id="demarcheurInfo" style="display:none; background:#e8f5e9; padding:10px; border-radius:6px; margin-bottom:15px;">
                    <p style="margin:0; font-size:13px; color:#2e7d32;"><strong>Option Démarcheur :</strong> Frais de mise en contact requis : <strong>9.300 FCFA</strong> pour accéder au numéro du vendeur.</p>
                </div>

                <div class="form-group">
                    <label>Contrat d'Utilisation E'Mob BF</label>
                    <div class="contract-box">
                        En vous inscrivant sur E'Mob BF, vous vous engagez à respecter les lois en vigueur au Burkina Faso concernant l'achat/vente de parcelles. Toute tentative de fraude entraînera des poursuites et la radiation définitive. Les commissions et frais de mise en contact sont dûs et non remboursables.
                    </div>
                    <label><input type="checkbox" required> J'accepte les termes du contrat</label>
                </div>

                <button type="submit" class="btn-submit">S'inscrire comme Acheteur</button>
            </form>
        </div>

        <!-- Section Vendeur -->
        <div id="vendeur" class="form-section">
            <h2>Espace Vendeur</h2>
            <form onsubmit="handleVendeur(event)">
                <div class="form-group">
                    <label>Nom et Prénom</label>
                    <input type="text" required placeholder="Votre nom complet">
                </div>
                <div class="form-group">
                    <label>Numéro de Téléphone</label>
                    <input type="tel" required placeholder="Votre numéro">
                </div>
                <div class="form-group">
                    <label>Numéro CNIB ou Passeport</label>
                    <input type="text" required placeholder="Votre pièce d'identité">
                </div>
                <div class="form-group">
                    <label>Zone / Lieu de la parcelle</label>
                    <input type="text" required placeholder="Ex: Ouagadougou, Saaba...">
                </div>
                <div class="form-group">
                    <label>Caractéristiques de la parcelle</label>
                    <select>
                        <option>Viabilisé</option>
                        <option>Non viabilisé</option>
                    </select>
                </div>
                <div class="form-group">
                    <label>Taille de la parcelle (m²)</label>
                    <input type="text" required placeholder="Ex: 300m²">
                </div>
                <div class="form-group">
                    <label>Document de la parcelle</label>
                    <input type="text" required placeholder="Ex: Attestation, Permis d'occuper, TF...">
                </div>
                <div class="form-group" style="background:#fff3e0; padding:10px; border-radius:6px;">
                    <label style="color:#e65100;">Rappel Commission (8% après vente)</label>
                    <p style="font-size:12px; margin:0;">Le paiement de la commission de 8% se fait directement via Mobile Money aux contacts du concepteur :<br>
                    • <strong>Orange Money :</strong> +226 55 48 57 51<br>
                    • <strong>Moov Money :</strong> +226 52 73 88 39</p>
                </div>

                <div class="form-group">
                    <label>Contrat Vendeur</label>
                    <div class="contract-box">
                        Je certifie être le propriétaire ou le mandataire légal de la parcelle mise en vente. Je m'engage à verser la commission obligatoire de 8% au concepteur après la vente effective de la parcelle via la plateforme E'Mob BF.
                    </div>
                    <label><input type="checkbox" required> J'accepte les termes du contrat</label>
                </div>

                <button type="submit" class="btn-submit">Publier ma parcelle</button>
            </form>
        </div>

        <!-- Section Visiteur -->
        <div id="visiteur" class="form-section">
            <h2>Espace Visiteur</h2>
            <form onsubmit="handleVisiteur(event)">
                <div class="form-group">
                    <label>Nom et Prénom</label>
                    <input type="text" required placeholder="Votre nom">
                </div>
                <div class="form-group">
                    <label>Numéro de Téléphone</label>
                    <input type="tel" required placeholder="Votre numéro">
                </div>
                <button type="submit" class="btn-submit">Accéder aux images des parcelles</button>
            </form>
        </div>
    </div>

    <script>
        function switchRole(roleId) {
            document.querySelectorAll('.form-section').forEach(el => el.classList.remove('active'));
            document.querySelectorAll('.role-btn').forEach(el => el.classList.remove('active'));
            
            document.getElementById(roleId).classList.add('active');
            event.target.classList.add('active');
        }

        function toggleDemarcheurFields() {
            const val = document.getElementById('isDemarcheur').value;
            document.getElementById('demarcheurInfo').style.display = val === 'oui' ? 'block' : 'none';
        }

        function handleAcheteur(e) {
            e.preventDefault();
            alert("Inscription acheteur enregistrée avec succès sur E'Mob BF !");
        }

        function handleVendeur(e) {
            e.preventDefault();
            alert("Parcelle enregistrée avec succès ! Pensez à régler la commission de 8% via OM (+226 55 48 57 51) ou Moov (+226 52 73 88 39) en cas de vente.");
        }

        function handleVisiteur(e) {
            e.preventDefault();
            alert("Bienvenue sur E'Mob BF ! Accès aux images autorisé.");
        }
    </script>
</body>
</html>
