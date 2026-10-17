# Turbo Rush 3D — projeto para gerar o APK

## Jeito mais fácil (sem instalar nada): GitHub Actions
1. Crie uma conta gratuita em github.com e um repositório novo (pode ser privado).
2. Envie TODOS os arquivos desta pasta para o repositório, mantendo a pasta oculta `.github`
   (no site: "Add file > Upload files" e arraste a pasta inteira).
3. Abra a aba **Actions > Build APK > Run workflow**. Em 5 a 10 minutos termina.
4. Dentro da execução, baixe o arquivo **TurboRush-APK** (um .zip com o `app-debug.apk`).
5. No celular, permita "instalar apps desconhecidos" e abra o APK.

## Jeito local (Windows/Mac/Linux)
Requisitos: Node 20, JDK 17 e Android Studio (com o Android SDK).
```
npm install
npm run three
npx cap add android
npx cap sync android
npx cap open android
```
No Android Studio: **Build > Build APK(s)**. O arquivo fica em `android/app/build/outputs/apk/debug/`.
Para travar em retrato, adicione `android:screenOrientation="portrait"` na tag `<activity>` do `AndroidManifest.xml`.

## Notas
- O jogo carrega o three.js de `www/three.min.js` (baixado pelo passo `npm run three`) e, se não achar,
  usa a internet como reserva.
- O APK gerado é de teste (debug) e serve para instalar no seu aparelho. Para publicar na Google Play
  é preciso assinar uma versão release (AAB) com sua chave.
- Anúncios: a função `showRewardedAd()` em `www/index.html` é um simulador. Troque pelo SDK real (AdMob)
  antes de publicar.
