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
            max-width: 650px;
            margin: 20px auto;
            background: white;
            padding: 20px;
            border-radius: 12px;
            box-shadow: 0 4px 12px rgba(0,0,0,0.05);
        }
        .roles-selector {
            display: flex;
            gap: 5px;
            margin-bottom: 20px;
            flex-wrap: wrap;
        }
        .role-btn {
            flex: 1;
            min-width: 100px;
            padding: 10px;
            border: 2px solid var(--primary);
            background: white;
            color: var(--primary);
            font-weight: bold;
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.3s;
            text-align: center;
            font-size: 13px;
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
        /* Style de la banque d'images / catalogue */
        .parcelle-card {
            border: 1px solid #ddd;
            border-radius: 8px;
            padding: 15px;
            margin-bottom: 15px;
            background: #fafafa;
        }
        .parcelle-images {
            display: flex;
            gap: 10px;
            overflow-x: auto;
            margin-top: 10px;
            padding-bottom: 5px;
        }
        .parcelle-images img {
            width: 120px;
            height: 90px;
            object-fit: cover;
            border-radius: 6px;
            border: 1px solid #ccc;
        }
    </style>
</head>
<body>

    <header>
        <h1>🏡 E'Mob BF</h1>
        <p>Vente et Achat de Parcelles au Burkina Faso (Intérieur & Diaspora)</p>
    </header>

    <div class="container">
        <div class="roles-selector">
            <button class="role-btn active" onclick="switchRole('acheteur')">Acheteur</button>
            <button class="role-btn" onclick="switchRole('vendeur')">Vendeur</button>
            <button class="role-btn" onclick="switchRole('visiteur')">Visiteur</button>
            <button class="role-btn" onclick="switchRole('catalogue')">Banque d'Images</button>
        </div>

        <!-- Section Acheteur -->
        <div id="acheteur" class="form-section active">
            <h2>Espace Acheteur</h2>
            <form onsubmit="handleAcheteur(event)">
                <div class="form-group">
                    <label>Nom et Prénom</label>
                    <input type="text" id="achNom" required placeholder="Ex: Koudougou Tewende Claude">
                </div>
                <div class="form-group">
                    <label>Numéro de Téléphone</label>
                    <input type="tel" id="achTel" required placeholder="Ex: +226 ...">
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
            <h2>Espace Vendeur & Publication</h2>
            <form onsubmit="handleVendeur(event)">
                <div class="form-group">
                    <label>Nom et Prénom</label>
                    <input type="text" id="vendNom" required placeholder="Votre nom complet">
                </div>
                <div class="form-group">
                    <label>Numéro de Téléphone</label>
                    <input type="tel" id="vendTel" required placeholder="Votre numéro">
                </div>
                <div class="form-group">
                    <label>Numéro CNIB ou Passeport</label>
                    <input type="text" required placeholder="Votre pièce d'identité">
                </div>
                <div class="form-group">
                    <label>Zone / Lieu de la parcelle</label>
                    <input type="text" id="vendZone" required placeholder="Ex: Ouagadougou, Saaba...">
                </div>
                <div class="form-group">
                    <label>Caractéristiques de la parcelle</label>
                    <select id="vendCaract">
                        <option value="Viabilisé">Viabilisé</option>
                        <option value="Non viabilisé">Non viabilisé</option>
                    </select>
                </div>
                <div class="form-group">
                    <label>Taille de la parcelle (m²)</label>
                    <input type="text" id="vendTaille" required placeholder="Ex: 300m²">
                </div>
                <div class="form-group">
                    <label>Document de la parcelle</label>
                    <input type="text" id="vendDoc" required placeholder="Ex: Attestation, Permis d'occuper, TF...">
                </div>
                <div class="form-group">
                    <label>Images de la parcelle (Galerie)</label>
                    <input type="file" id="parcelleImagesInput" accept="image/*" multiple required>
                    <small style="color: #666; font-size: 11px;">Ajoutez des photos visibles par les visiteurs et acheteurs.</small>
                </div>

                <div class="form-group" style="background:#fff3e0; padding:10px; border-radius:6px;">
                    <label style="color:#e65100;">Rappel Commission (8% après vente)</label>
                    <p style="font-size:12px; margin:0;">Paiement de la commission via Mobile Money aux contacts du concepteur :<br>
                    • <strong>Orange Money :</strong> +226 55 48 57 51<br>
                    • <strong>Moov Money :</strong> +226 52 73 88 39</p>
                </div>

                <div class="form-group">
                    <label>Contrat Vendeur</label>
                    <div class="contract-box">
                        Je certifie être le propriétaire ou le mandataire légal de la parcelle. Je m'engage à verser la commission obligatoire de 8% au concepteur après la vente effective via E'Mob BF.
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
                <button type="submit" class="btn-submit">Accéder à la Banque d'Images</button>
            </form>
        </div>

        <!-- Section Banque d'Images / Catalogue Public -->
        <div id="catalogue" class="form-section">
            <h2>Banque d'Images & Parcelles Disponibles</h2>
            <p style="font-size: 13px; color: #666;">Voici toutes les parcelles enregistrées par les vendeurs à travers le Burkina Faso.</p>
            <div id="parcellesList">
                <p style="text-align: center; color: #888;">Aucune parcelle enregistrée pour le moment. Soyez le premier vendeur à publier !</p>
            </div>
        </div>
    </div>

    <script>
        // Charger les parcelles enregistrées depuis la mémoire du navigateur
        let parcelles = JSON.parse(localStorage.getItem('emob_parcelles')) || [];

        function switchRole(roleId) {
            document.querySelectorAll('.form-section').forEach(el => el.classList.remove('active'));
            document.querySelectorAll('.role-btn').forEach(el => el.classList.remove('active'));
            
            document.getElementById(roleId).classList.add('active');
            event.target.classList.add('active');

            if(roleId === 'catalogue') {
                afficherCatalogue();
            }
        }

        function toggleDemarcheurFields() {
            const val = document.getElementById('isDemarcheur').value;
            document.getElementById('demarcheurInfo').style.display = val === 'oui' ? 'block' : 'none';
        }

        function handleAcheteur(e) {
            e.preventDefault();
            alert("Inscription acheteur réussie ! Vous pouvez maintenant consulter la Banque d'Images.");
            switchRole('catalogue');
        }

        function handleVisiteur(e) {
            e.preventDefault();
            alert("Accès autorisé ! Bienvenue dans la Banque d'Images E'Mob BF.");
            switchRole('catalogue');
        }

        function handleVendeur(e) {
            e.preventDefault();
            const filesInput = document.getElementById('parcelleImagesInput');
            let imagesArray = [];

            if (filesInput.files.length > 0) {
                let filesProcessed = 0;
                Array.from(filesInput.files).forEach(file => {
                    const reader = new FileReader();
                    reader.onload = function(event) {
                        imagesArray.push(event.target.result);
                        filesProcessed++;
                        if (filesProcessed === filesInput.files.length) {
                            sauvegarderParcelle(imagesArray);
                        }
                    };
                    reader.readAsDataURL(file);
                });
            } else {
                sauvegarderParcelle([]);
            }
        }

        function sauvegarderParcelle(images) {
            const nouvelleParcelle = {
                nom: document.getElementById('vendNom').value,
                tel: document.getElementById('vendTel').value,
                zone: document.getElementById('vendZone').value,
                caract: document.getElementById('vendCaract').value,
                taille: document.getElementById('vendTaille').value,
                doc: document.getElementById('vendDoc').value,
                images: images
            };

            parcelles.push(nouvelleParcelle);
            localStorage.setItem('emob_parcelles', JSON.stringify(parcelles));

            alert("Parcelle publiée avec succès ! Elle est désormais visible dans la Banque d'Images.\n\nRappel Commission 8% :\n- Orange Money : +226 55 48 57 51\n- Moov Money : +226 52 73 88 39");
            document.querySelector('#vendeur form').reset();
            switchRole('catalogue');
        }

        function afficherCatalogue() {
            const container = document.getElementById('parcellesList');
            if (parcelles.length === 0) {
                container.innerHTML = `<p style="text-align: center; color: #888;">Aucune parcelle enregistrée pour le moment.</p>`;
                return;
            }

            let html = '';
            parcelles.forEach((p, index) => {
                let imagesHtml = '';
                if (p.images && p.images.length > 0) {
                    p.images.forEach(img => {
                        imagesHtml += `<img src="${img}" alt="Parcelle">`;
                    });
                } else {
                    imagesHtml = `<p style="font-size:12px; color:#888;">Aucune image fournie</p>`;
                }

                html += `
                    <div class="parcelle-card">
                        <h3 style="margin: 0 0 5px 0; color: var(--primary);">📍 ${p.zone}</h3>
                        <p style="margin: 3px 0; font-size: 13px;"><strong>Taille :</strong> ${p.taille} | <strong>État :</strong> ${p.caract}</p>
                        <p style="margin: 3px 0; font-size: 13px;"><strong>Document :</strong> ${p.doc}</p>
                        <p style="margin: 3px 0; font-size: 13px; color: #555;"><strong>Vendeur :</strong> ${p.nom} (${p.tel})</p>
                        <div class="parcelle-images">
                            ${imagesHtml}
                        </div>
                    </div>
                `;
            });
            container.innerHTML = html;
        }
    </script>
</body>
</html>                                                             
