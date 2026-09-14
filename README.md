# Perdido em Palmeira

## Configuração

Edite [`config.js`](config.js):

1. **Maps**: cole sua chave da Maps JavaScript API em `GOOGLE_MAPS_API_KEY`.
   Restrinja por referenciador HTTP: `https://SEUUSUARIO.github.io/*`.

2. **Login + registro de partidas** (opcional): crie um projeto em
   [console.firebase.google.com](https://console.firebase.google.com), ative
   **Authentication → Google** e **Firestore Database**. Em Configurações do
   projeto → Seus apps → Web, copie os valores para `FIREBASE_CONFIG`.

   Em Firestore → Regras, use:

   ```
   rules_version = '2';
   service cloud.firestore {
     match /databases/{database}/documents {
       match /plays/{playId} {
         allow create: if request.auth != null;
         allow read, update, delete: if false;
       }
     }
   }
   ```

   Sem isso configurado, o jogo funciona normalmente, só sem exigir login.
   Os resultados ficam visíveis na coleção `plays` do Firestore.
