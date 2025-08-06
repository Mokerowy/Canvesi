<template>
  <section class="section services-section" id="services">
    <div class="content-wrapper">
        <h2>Unsere Dienstleistungen im Detail</h2>
        <p class="section-intro">
            Wir bieten ein umfassendes Spektrum an Webentwicklungsdiensten, um Ihre Online-Präsenz von Grund auf aufzubauen oder zu optimieren. Unser Fokus liegt darauf, maßgeschneiderte Lösungen zu schaffen, die Leistung, Sicherheit und ein herausragendes Benutzererlebnis vereinen.
        </p>

        <div class="service-details">
            <ul>
                <li>
                    <strong>Professionelles Webdesign und UX/UI:</strong> Wir entwerfen intuitive, responsive und visuell ansprechende Benutzeroberflächen, die auf allen Geräten perfekt funktionieren.
                </li>
                <li>
                    <strong>Entwicklung mit modernen Technologien:</strong> Wir entwickeln performante und skalierbare Websites und Anwendungen, die auf den neuesten Webstandards basieren.
                </li>
                <li>
                    <strong>Suchmaschinenoptimierung (SEO):</strong> Wir integrieren bewährte SEO-Strategien direkt in den Entwicklungsprozess, um sicherzustellen, dass Ihre Website von potenziellen Kunden gefunden wird.
                </li>
                <li>
                    <strong>Wartung und technischer Support:</strong> Wir bieten umfassende Unterstützung nach dem Launch, einschließlich regelmäßiger Updates, Sicherheitsüberwachung und technischem Support.
                </li>
                <li>
                    <strong>E-Commerce-Lösungen:</strong> Wir entwickeln leistungsstarke Online-Shops, die einfach zu verwalten und für Ihre Kunden angenehm zu nutzen sind.
                </li>
            </ul>
        </div>
        <p class="section-outro">
            Benötigen Sie eine individuelle Lösung, die hier nicht aufgeführt ist? <a href="#contact">Kontaktieren Sie uns</a>, um Ihre spezifischen Anforderungen zu besprechen.
        </p>
    </div>
</section>
</template>

<style scoped>
.services-section {
  background-color: rgba(5, 5, 5, 0.42);
  pointer-events: none;
  padding: 40px 20px; 

}

.services-section * {
  pointer-events: auto;
}

/* Neuer Wrapper-Container für den Inhalt */
.content-wrapper {
  max-width: 1000px; /* Maximale Breite des Inhalts */
  margin: 0 auto; /* Zentriert den Inhalt */
  color: #f0f0f0;
}

h2 {
  text-align: center;
  font-size: 2.5rem;
  margin-bottom: 20px;
  color: #ffffff;
}

.services-section h3 {
  color: #ececec;
  margin-top: 0;
  margin-bottom: 10px;
}

.section-intro {
  text-align: center;
  max-width: 800px;
  margin: 0 auto 40px auto;
  line-height: 1.6;
  font-size: 1.1rem;
}

.service-process,
.service-support {
  background-color: rgba(255, 255, 255, 0.05);
  padding: 25px;
  border-radius: 8px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  margin-bottom: 30px;
}

.service-support {
  margin-bottom: 0;
}

p {
  line-height: 1.6;
  margin-bottom: 15px;
}
</style>