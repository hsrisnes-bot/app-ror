[globals.css](https://github.com/user-attachments/files/22146900/globals.css)[index.tsx](https://github.com/user-attachments/files/22146898/index.tsx)[_app.tsx](https://github.com/user-attachments/files/22146897/_app.tsx)[AvlopsrorApp.tsx](https://github.com/user-attachments/files/22146894/AvlopsrorApp.tsx)
import { useState } from "react";
import { jsPDF } from "jspdf";

export default fconst nextConfig = {};
module.exports {
  "name": "rorapp",
  "version": "1.0.0",
  "private": true,[import '@/styles/globals.css'
import type { AppProps } from 'next/app'

export defaul# Rørapp 🚰

En Next.js-appmodule.exports = {
  content: [
    "./pages/**/*.{js,ts,jsx,tsx}",
    "./components/**/*.{js,ts,jsx,tsx}",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
};
[tailwind.config.js](https://github.com/user-attachments/files/22146901/tailwind.config.js)
 for enkel håndtering av avløpsrør-data, med støtte for PDF-generering.
[Uploading gl@tailwind base;
@tailwind components;
@tailwind utilities;

body {
  @apply bg-gray-50 text-gray-900;
}
obals.css…]()

## 🚀 Kom i gang

### 1. Installer avhengigheter
```bash
npm install
```

### 2. Kjør lokalt
```bash
npm run dev
```
Appen vil kjøre på [http://localhost:3000](http://localhost:3000).

### 3. Bygg for produksjon
```bash
npm run build
npm start
```

### 4. Deploy til Vercel
1. Opprett et nytt repo på GitHub (f.eks. `rorapp`).
2. Push alle filene til GitHub.
3. Gå til [https://vercel.com/new](https://vercel.com/new).
4. Velg GitHub-repoet ditt og trykk *Deploy*.

Vercel vil automatisk bygge og kjøre appen.

---

## 📂 Struktur
```
/pages          → Next.js-sider (index.tsx viser AvlopsrorApp)
/components     → AvlopsrorApp-komponenten med PDF-funksjon
/styles         → Tailwind-stilark
/public         → Statisk innhold
```

## 🛠 Funksjoner
- Legg til avløpspunkter i en liste
- Generer en PDF-rapport med punktene
- Bygget på Next.js + React + TailwindCSS + jsPDF

## 👷 Videre arbeid
- Legge til database for lagring av prosjekter
- Flere eksportformater (Excel, Word)
- Brukerinnlogging
[README.md](https://github.com/user-attachments/files/22146899/README.md)
t function App({ Component, pageProps }: AppProps) {
  return <Component {...pageProps} />
}[Uplimport AvlopsrorApp from "../components/AvlopsrorApp";

export default function Home() {
  return <AvlopsrorApp />;
}
oading index.tsx…]()

Uploading _app.tsx…]()

  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start"
  },
  "dependencies": {
    "next": "14.2.4",
    "react": "18.2.0",
    "react-dom": "18.2.0",
    "jspdf": "2.5.1",
    "tailwindcss": "3.4.1"
  }
}[package.json](https://github.com/user-attachments/files/22146896/package.json)
= nextConfig;
[next.config.js](https://github.com/user-attachments/files/22146895/next.config.js)
unction AvlopsrorApp() {
  const [points, setPoints] = useState<string[]>([]);

  const addPoint = () => {
    const newPoint = `Avløpspunkt ${points.length + 1}`;
    setPoints([...points, newPoint]);
  };

  const generatePDF = () => {
    const doc = new jsPDF();
    doc.setFontSize(18);
    doc.text("Røroppsett rapport", 20, 20);
    doc.setFontSize(12);
    points.forEach((p, i) => {
      doc.text(`${i + 1}. ${p}`, 20, 40 + i * 10);
    });
    doc.save("rapport.pdf");
  };

  return (
    <div className="p-6 max-w-xl mx-auto bg-white shadow rounded-2xl">
      <h1 className="text-2xl font-bold mb-4">Avløpsrør App</h1>
      <button
        onClick={addPoint}
        className="bg-blue-600 text-white px-4 py-2 rounded-lg mr-2"
      >
        Legg til avløpspunkt
      </button>
      <button
        onClick={generatePDF}
        className="bg-green-600 text-white px-4 py-2 rounded-lg"
      >
        Generer PDF
      </button>
      <ul className="mt-4 list-disc list-inside">
        {points.map((p, i) => (
          <li key={i}>{p}</li>
        ))}
      </ul>
    </div>
  );
}
