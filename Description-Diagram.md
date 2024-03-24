# Penjelasan Diagram

**Core Banking System (CBS)** merupakan fondasi utama dari infrastruktur **SOA** di organisasi tersebut. **SOA** memecah aplikasi menjadi komponen-komponen terpisah yang disebut layanan, yang berkomunikasi melalui antarmuka yang terdefinisi dengan baik, memungkinkan **reusability** dan **modularitas** yang tinggi.

**Spring Boot** digunakan sebagai kerangka kerja untuk mengembangkan layanan-layanan ini. Setiap layanan **Spring Boot** yang terintegrasi dengan **CBS** dan didokumentasikan menggunakan **OpenAPI**. Hal ini memungkinkan komunikasi antara layanan-layanan tersebut melalui antarmuka yang terdefinisi dengan baik, meningkatkan **reusability** dan **scalability**.

Layanan-layanan ini dijalankan di lingkungan **OpenShift**, sebuah platform yang memungkinkan pengelolaan dan pen-skalaan aplikasi dalam lingkungan container. Manajemen layanan ini dilakukan dengan bantuan **Jenkins**, alat otomatisasi yang mengotomatisasi proses pengembangan dan penyebaran perangkat lunak.

Sementara itu, untuk meningkatkan pengalaman pengguna pada aplikasi web, **Service Worker** diimplementasikan. Ini memberikan kemampuan aplikasi untuk menyediakan fungsionalitas seperti cache, pemberitahuan push, dan pengelolaan tugas latar belakang, yang meningkatkan kinerja dan memberikan kemampuan untuk bekerja secara offline.

Pemantauan dan analisis log dari layanan-layanan di **OpenShift** dilakukan menggunakan **Kibana**, memberikan wawasan tentang kinerja sistem dan perilaku pengguna. Fitur snpashot dan restore dalam **Kibana** sangat membantu dalam membantu backup index log secara berkala.

Dengan demikian, infrastruktur teknologi di organisasi tersebut terintegrasi dengan baik, dimulai dari fondasi **SOA** hingga layanan-layanan aplikasi web yang ditingkatkan oleh **Service Worker**. Semua ini dikelola dan diintegrasikan menggunakan alat-alat seperti **OpenAPI**, **Jenkins**, dan **Kibana**, serta dijalankan di atas platform **OpenShift** yang fleksibel dan skalabel.
