⚡ Guía de Instalación y Ejecución

Para correr este proyecto localmente, necesitarás tener instalado Node.js.
1. Clonar el repositorio
Bash

git clone [https://github.com/tu-usuario/buscadorDemo.git](https://github.com/tu-usuario/buscadorDemo.git)
cd buscadorDemo

2. Iniciar el Backend (Puerto 3001)

Abre una terminal y ejecuta:
Bash

cd server
npm install
node index.js

Deberías ver: ✅ Servidor corriendo en: http://localhost:3001
3. Iniciar el Frontend (Puerto 5173)

Abre otra terminal y ejecuta:
Bash

cd client
npm install
npm run dev

Abre tu navegador en http://localhost:5173
🧠 Arquitectura Lógica (Para replicar en Angular/Otros)

Si deseas migrar esta lógica a otro framework, sigue estos principios:
1. Búsqueda Federada (Backend)

No realices búsquedas secuenciales. Utiliza promesas paralelas para reducir la latencia.

Patrón recomendado:
JavaScript

// Malo (Waterfall): Tarda A + B
const dataA = await serviceA.search();
const dataB = await serviceB.search();

// Bueno (Parallel): Tarda max(A, B)
const [dataA, dataB] = await Promise.all([
  serviceA.search(),
  serviceB.search()
]);

2. Normalización (Backend)

El Frontend debe ser agnóstico a la fuente de datos. El Backend debe transformar cualquier respuesta externa (S3, SAP, Salesforce) a un modelo canónico unificado: { id, name, description, category, tags }.
3. Debounce (Frontend)

Evita saturar el servidor. Implementa un retraso en la captura del input del usuario.

    React: useEffect con setTimeout.

    Angular: RxJS con el operador debounceTime(300).

🧪 Pruebas Recomendadas

    Búsqueda Directa: Buscar "tubos" y verificar resaltado.

    Contexto: Buscar "microscopio" y verificar que aparezca el "Manual" en la barra lateral.

    Filtros: Verificar que los botones de categoría limpien la lista.

    Modo Oscuro: Cambiar el tema y verificar legibilidad.
