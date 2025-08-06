<template>
  <section class="section contact-section" id="contact">
    <h2 class="contact-title">
      Kontaktieren Sie uns  Lassen Sie uns über Ihr Projekt sprechen!
    </h2>
    <p>
  Haben Sie Fragen zu Ihrem Online-Auftritt? Brauchen Sie eine neue Website? Füllen Sie das Formular aus, und wir melden uns bei Ihnen.
    </p>

    <form class="contact-form" action="https://formspree.io/f/mwpqrzpe" method="POST">
      <div class="form-columns">
        <div class="form-group">
          <label for="name">Ihr Name und Nachname:</label>
          <input
            type="text"
            id="name"
            name="name"
            placeholder="Max Mustermann"
            required
          />
        </div>
        <div class="form-group">
          <label for="email">Ihre E-Mail-Adresse:</label>
          <input
            type="email"
            id="email"
            name="email"
            placeholder="info@ihrefirma.de"
            required
          />
        </div>
      </div>

      <div class="form-columns">
        <div class="form-group">
          <label for="company">Ihr Firmenname (optional):</label>
          <input
            type="text"
            id="company"
            name="company"
            placeholder="ABC GmbH"
          />
        </div>
        <div class="form-group">
          <label for="phone">Ihre Telefonnummer (optional):</label>
          <input
            type="tel"
            id="phone"
            name="phone"
            placeholder="+49 XXX XXX XXX"
          />
        </div>
      </div>

      <div class="form-group">
        <label for="subject">Worum geht es bei Ihrer Anfrage?</label>
        <select id="subject" name="subject">
          <option value="">-- Bitte Thema wählen --</option>
          <option value="Neue Webseite">Neue Webseite</option>
          <option value="Website-Relaunch / Redesign">
            Website-Relaunch / Redesign
          </option>
          <option value="Onlineshop / E-Commerce">
            Onlineshop / E-Commerce
          </option>
          <option value="SEO-Optimierung / Marketing">
            SEO-Optimierung / Marketing
          </option>
          <option value="Technischer Support">Technischer Support</option>
          <option value="Sonstiges">Sonstiges</option>
        </select>
      </div>
      <div class="form-group">
        <label for="message"
          >Beschreiben Sie kurz Ihr Projekt oder Ihre Frage:</label
        >
        <textarea
          id="message"
          name="message"
          rows="6"
          placeholder="Hier können Sie Ihr Anliegen oder Ihre Frage beschreiben..."
          required
        ></textarea>
      </div>
      <button type="submit" class="submit-button">Anfrage senden</button>
    </form>

    <div class="contact-info">
      <h3>Sie benötigen schnellen Kontakt?</h3>
      <p>
        E-Mail:
        <a href="mailto:canvesidigital@gmail.com">canvesidigital@gmail.com</a>
      </p>
      <p>Telefon: <a href="tel:+4915781939666">+4915781939666</a></p>

      <div class="social-links">
        <a href="#" aria-label="Facebook"><i class="fab fa-facebook-f"></i></a>
        <a href="#" aria-label="LinkedIn"><i class="fab fa-linkedin"></i></a>
        <a href="#" aria-label="Instagram"><i class="fab fa-instagram"></i></a>
        <img
          class="logoFooter"
          src="../../public/DigitalCanvesi.svg"
          alt="Logo der Firma Canvesi"
        />
      </div>
    </div>
  </section>
</template>
<style>
.contact-section h2 {
  color: #e0ffff;
  text-align: center;
  margin-bottom: 30px;
  font-size: 2.8rem;
  text-shadow: 0 0 15px rgba(170, 230, 255, 0.7);
}

.contact-section p {
  margin-bottom: 40px;
  color: #b0d9e7;
  text-align: center;
  max-width: 800px;
  margin-left: auto;
  margin-right: auto;
  line-height: 1.6;
}

.contact-form {
  position: relative;
  max-width: 900px;
  margin: 0 auto 60px auto;
  text-align: left;
  padding: 40px;

  border-radius: 20px;

}


.contact-form::before,
.contact-form::after {
  content: "";
  position: absolute;
  left: 0;
  width: 100%;
  height: 2px; 
}


.contact-form::before {
  top: 0;
  box-shadow: 0 2px 4px rgba(170, 230, 255, 0.7);
}


.contact-form::after {
  bottom: 0;
  box-shadow: 0 -2px 4px rgba(170, 230, 255, 0.7); 
}


.form-columns {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 25px;
}

.form-group {
  margin-bottom: 25px;
}



.form-group label {
  display: block;
  margin-bottom: 10px;
  color: rgb(255, 255, 255);
  font-weight: bold;
  font-size: 1.15rem;
  text-shadow: 0 0 8px rgba(170, 230, 255, 0.7);
}


.form-group input[type="text"],
.form-group input[type="email"],
.form-group input[type="tel"],
.form-group select,
.form-group textarea {
  width: 100%;
  padding: 16px 20px;
  background-color: rgba(30, 30, 30, 0.8);
  border: 2px solid rgb(255, 255, 255);
  border-radius: 10px;
  color: #e0ffff;
  font-size: 1.05rem;
  outline: none;
  transition: border-color 0.4s ease, box-shadow 0.4s ease,
    background-color 0.4s ease;
  box-sizing: border-box;
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
}



.form-group input::placeholder,
.form-group textarea::placeholder {
  color: rgba(170, 230, 255, 0.6);
}

.form-group input[type="text"]:focus,
.form-group input[type="email"]:focus,
.form-group input[type="tel"]:focus,
.form-group select:focus,
.form-group textarea:focus {
  border-color: rgb(255, 255, 255);
  box-shadow: 0 0 20px rgba(255, 255, 255, 0.8),
    0 0 10px rgba(102, 224, 255, 0.6);
  background-color: rgba(40, 40, 40, 0.9);
}

.form-group textarea {
  resize: vertical;
  min-height: 90px;
}

.submit-button {
  display: block;
  margin: 0 auto;
  padding: 18px 40px;
  background-color: rgba(104, 104, 104,0.3);
  color: #e0ffff;
  border: 2px solid #e0ffff;
  border-radius: 50px;
  font-size: 1.3rem;
  font-weight: bold;
  cursor: pointer;
  transition: background-color 0.5s ease, color 0.5s ease, box-shadow 0.5s ease,
    transform 0.3s ease;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  position: relative;
  overflow: hidden;
}

.submit-button:hover {
  background-color: #ffffff;
  box-shadow: 0 0 20px rgba(255, 255, 255, 0.8),
    0 0 10px rgba(102, 224, 255, 0.6);
  color: #000000;
}

.submit-button:active {
  transform: translateY(0);
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
}


.contact-info {
  text-align: center;
  color: #b0d9e7;
}

.contact-info h3 {
  margin-bottom: 25px;
  color: #e0ffff;
  font-size: 1.8rem;
  text-shadow: 0 0 10px rgba(170, 230, 255, 0.6);
}

.contact-info p {
  font-size: 1.1rem;
  margin-bottom: 18px;
}

.social-links {
  margin-top: 10px;
  display: flex;
  justify-content: center;
  gap: 35px;
  padding-bottom: 20px;
  align-items: center; 
}

.social-links a {
  font-size: 2.5rem;
  color: rgb(102, 224, 255);
  transition: color 0.3s ease, text-shadow 0.3s ease, transform 0.3s ease;
  border-bottom: none;
}

.social-links a:hover {
  color: rgb(255, 255, 255);
  text-shadow: 0 0 20px rgba(255, 255, 255, 1);
  transform: scale(1.1);
}

.logoFooter {
  height: auto;
  max-width: 200px;
  display: block;
  margin-top: 20px;
}




@media (max-width: 992px) {
  .contact-form {
    padding: 30px;
  }
  .contact-section h2 {
    font-size: 2.2rem;
  }
}


@media (max-width: 768px) {
  .contact-form {
    padding: 25px;
    margin-bottom: 40px;
    max-width: none;

    margin: 0;
  }
  .contact-section h2 {
    font-size: 1.8rem;
  }
  .form-columns {
    grid-template-columns: 1fr;
    gap: 0;
  }
  .form-group label {
    font-size: 1rem;
    margin-bottom: 8px;
  }
  .form-group input[type="text"],
  .form-group input[type="email"],
  .form-group input[type="tel"],
  .form-group select,
  .form-group textarea {
    padding: 12px 15px;
    font-size: 0.95rem;
  }
  .form-group textarea {
    max-height: 50px;
  }
  .submit-button {
    width: 100%;
    padding: 15px 25px;
    font-size: 1.1rem;
  }

  .contact-info h3 {
    font-size: 1.5rem;
  }
  .contact-info p {
    font-size: 1rem;
  }
  .social-links {
    flex-wrap: wrap;
    gap: 20px;
    margin-top: 25px;
  }
  .social-links a {
    font-size: 2rem;
  }
}

@media (max-width: 480px) {
  .contact-section {
    padding-top: 60px;
    padding-bottom: 60px;
  }
  .contact-form {
    padding: 35px 15px;
  }
}

@media (min-width: 769px) {
  .form-columns {
    margin-bottom: 25px;
  }
  .form-columns .form-group {
    margin-bottom: 0;
  }
}
@media (min-width: 1300px) {
  .section h2 {
    margin: 0 100px 30px 100px;
  }
}

</style>
