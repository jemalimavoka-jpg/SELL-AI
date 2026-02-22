<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>SELL AI Auto-Interactif</title>
<style>
body{font-family:Arial,sans-serif;margin:0;padding:20px;background:#f9f9f9;}
h1,h2{color:#333;}
input,textarea,button{width:100%;padding:10px;margin:5px 0;font-size:16px;}
button{background:#2196F3;color:white;border:none;border-radius:5px;cursor:pointer;transition:0.2s;}
button:hover{background:#0b7dda;}
.box{background:white;padding:15px;margin:10px 0;border-radius:8px;box-shadow:0 0 5px rgba(0,0,0,0.1);}
.history-item{border:1px solid #ccc;padding:10px;margin:10px 0;border-radius:5px;background:#fff;}
</style>
</head>
<body>

<h1>SELL AI Auto-Interactif</h1>

<div class="box">
<h2>Produit à promouvoir</h2>
<input type="text" id="product" placeholder="Produit (ex: Radio Bluetooth)">
<input type="text" id="audience" placeholder="Audience cible (ex: jeunes, gamers)">
<input type="text" id="objective" placeholder="Objectif (ex: vendre plus)">
<button onclick="startAutoInteraction()">Lancer Auto-Interaction</button>
</div>

<div class="box">
<h2>Historique & Interactions</h2>
<div id="history"></div>
</div>

<script>
// Générer contenu viral simple
function generateContent(product,audience,objective){
    const hooks=["Accroche choc!","Imagine ça…","Tu ne croiras jamais…","Attention, ceci change tout!","Le secret que personne ne dit…"];
    const dramas=["Un client presque perdu…","Une histoire drôle de vente…","Un moment embarrassant…","Quand tout semblait perdu…","Une surprise inattendue…"];
    const questions=["Et toi, que ferais-tu?","Qui est concerné ici?","Est-ce que tu l’avais vu venir?","Comment réagirais-tu?","As-tu déjà vécu ça?"];
    const responses=["Merci pour ton commentaire!","Intéressant, qu’en penses-tu?","On peut t’aider avec ça!","Bonne question!","Voici ma réponse…"];

    return {
        content:`Hooks: ${hooks.join(", ")}\nDramas: ${dramas.join(", ")}\nQuestions: ${questions.join(", ")}\nRéponses types: ${responses.join(", ")}`,
        hooks,dramas,questions,responses
    };
}

// Générer commentaires automatiquement
function generateComments(contentObj){
    const randomHook = contentObj.hooks[Math.floor(Math.random()*contentObj.hooks.length)];
    const randomDrama = contentObj.dramas[Math.floor(Math.random()*contentObj.dramas.length)];
    const randomQuestion = contentObj.questions[Math.floor(Math.random()*contentObj.questions.length)];
    return [
        `J'adore! ${randomHook}`,
        `Wow ${randomDrama}`,
        `Et sinon ${randomQuestion}?`
    ];
}

// Générer réponses IA pour les commentaires
function generateResponses(comments,contentObj){
    return comments.map(c=>`${c} → ${contentObj.responses[Math.floor(Math.random()*contentObj.responses.length)]}`);
}

// Sauvegarder dans localStorage
function saveHistory(product,audience,objective,comments,responses){
    let history=JSON.parse(localStorage.getItem('sell_ai_auto_history')||'[]');
    history.unshift({product,audience,objective,comments,responses,date:new Date().toLocaleString()});
    localStorage.setItem('sell_ai_auto_history',JSON.stringify(history));
    renderHistory();
}

// Afficher historique
function renderHistory(){
    const history=JSON.parse(localStorage.getItem('sell_ai_auto_history')||'[]');
    const container=document.getElementById('history');
    container.innerHTML='';
    history.forEach(h=>{
        const div=document.createElement('div');
        div.className='history-item';
        div.innerHTML=`<strong>${h.product}</strong> (${h.date})<br>Audience: ${h.audience}<br>Objectif: ${h.objective}<br>
        <strong>Commentaires générés:</strong><br>${h.comments.join("<br>")}<br>
        <strong>Réponses IA:</strong><br>${h.responses.join("<br>")}`;
        container.appendChild(div);
    });
}

// Fonction principale pour lancer l’auto-interaction
function startAutoInteraction(){
    const product=document.getElementById('product').value;
    const audience=document.getElementById('audience').value;
    const objective=document.getElementById('objective').value;
    if(!product || !audience) return alert('Produit et audience requis');

    const contentObj=generateContent(product,audience,objective);
    const comments=generateComments(contentObj);
    const responses=generateResponses(comments,contentObj);
    saveHistory(product,audience,objective,comments,responses);

    // Boucle automatique toutes les 10 secondes pour simuler interactions continues
    setInterval(()=>{
        const newComments=generateComments(contentObj);
        const newResponses=generateResponses(newComments,contentObj);
        saveHistory(product,audience,objective,newComments,newResponses);
    },10000);
}

// Initialisation
renderHistory();
</script>

</body>
</html>
