# Vercel Deployment Setup

## Ortam Değişkenlerini Ayarla

Vercel dashboard'da aşağıdaki adımları takip et:

### 1. Vercel Dashboard'a Git
- https://vercel.com/dashboard adresine git
- Projenin settings > "Environment Variables" bölümüne gir

### 2. Environment Variables Ekle

Aşağıdaki değişkenleri ekle (kendi API key'lerini kullan):

```
GEMINI_API_KEY=your_gemini_api_key_here
GROQ_API_KEY=your_groq_api_key_here
```

#### Google Gemini API Key nasıl alınır?
1. https://aistudio.google.com/app/apikey adresine git
2. "Create API Key" butonuna tıkla
3. Üretilen key'i kopyala

#### Groq API Key nasıl alınır?
1. https://console.groq.com/keys adresine git
2. "Create API Key" butonuna tıkla
3. Üretilen key'i kopyala

### 3. Redeploy
- Environment variables ekledikten sonra Vercel otomatik redeploy yapmaz
- Vercel Dashboard → Deployments → "Redeploy" butonuna tıkla
- veya GitHub repo'ya boş bir commit push et:
  ```bash
  git commit --allow-empty -m "Trigger redeploy with env vars"
  git push origin main
  ```

## Test Et

Vercel deploy tamamlandıktan sonra:
- https://your-app.vercel.app/ ziyaret et
- Tarayıcı console'unda (F12) hata varsa kontrol et
- https://your-app.vercel.app/api/health endpoint'i test et

## Sorun Giderme

### "Not Found" Hatası
- `vercel.json` route'lar doğru mu kontrol et
- Vercel build logs'unda hata var mı kontrol et

### API çağrıları başarısız
- Environment variables ayarlanmış mı kontrol et
- API key'ler geçerli mi test et
- Vercel logs'unda database hatası var mı kontrol et

### Beyaz ekran
- Tarayıcı console'unu aç (F12 → Console)
- JavaScript hatası var mı kontrol et
