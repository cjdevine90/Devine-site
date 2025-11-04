'use client';
import React from "react";

/**
 * Courtney Devine — Official Site (React/TSX)
 * Fix: convert HTML to valid TSX to resolve “Unexpected token (1:0)” at /index.tsx.
 * Images live in /public/assets/... (Next.js) or /assets/... (static host).
 * Contact form uses a Formspree placeholder — replace the action with your endpoint.
 */

/* ---------- helpers ---------- */
const Section: React.FC<{ id?: string; style?: React.CSSProperties; children: React.ReactNode }> =
  ({ id, style, children }) => (
    <section id={id} style={{ maxWidth: 1120, margin: "0 auto", padding: "64px 24px", ...(style || {}) }}>
      {children}
    </section>
  );

const Grid: React.FC<{ children: React.ReactNode }> = ({ children }) => (
  <div style={{ display: "grid", gap: 24, gridTemplateColumns: "repeat(auto-fit, minmax(300px, 1fr))" }}>
    {children}
  </div>
);

const Card: React.FC<{ children: React.ReactNode }> = ({ children }) => (
  <div style={{ background: "rgba(255,255,255,.06)", border: "1px solid rgba(255,255,255,.15)", borderRadius: 16, padding: 24 }}>
    {children}
  </div>
);

const Img: React.FC<{ src: string; alt: string; style?: React.CSSProperties }> = ({ src, alt, style }) => (
  <img src={src} alt={alt} style={{ width: "100%", borderRadius: 12, border: "1px solid rgba(255,255,255,.2)", ...(style || {}) }} />
);

/* ---------- page ---------- */
export default function Page() {
  // tiny runtime “tests”
  console.assert(typeof window !== "undefined", "TSX renders on client");
  console.assert(["/assets/hero-cover.jpg", "/assets/courtney-portrait.jpg"].every(Boolean), "image paths must be non-empty");

  const bodyStyle: React.CSSProperties = {
    background: "linear-gradient(to bottom,#000,#0B0F1A,#000)",
    color: "#fff",
    fontFamily: "Arial, sans-serif",
  };

  const buttonStyle: React.CSSProperties = {
    borderRadius: 16,
    background: "linear-gradient(to right,#ec4899,#a855f7,#f59e0b)",
    color: "#000",
    fontWeight: 700,
    padding: "12px 20px",
    textDecoration: "none",
    display: "inline-block",
  };

  return (
    <div style={bodyStyle}>
      {/* HEADER */}
      <header style={{ position: "sticky", top: 0, zIndex: 50, backdropFilter: "blur(6px)", background: "rgba(0,0,0,.5)", borderBottom: "1px solid rgba(255,255,255,.1)" }}>
        <div style={{ maxWidth: 1120, margin: "0 auto", padding: "16px 24px", display: "flex", justifyContent: "space-between", alignItems: "center" }}>
          <a href="#home" style={{ fontWeight: 600, letterSpacing: 1 }}>COURTNEY DEVINE</a>
          <nav>
            <a href="#about" style={{ marginRight: 16, color: "#fff", textDecoration: "none" }}>About</a>
            <a href="#meet-claire" style={{ marginRight: 16, color: "#fff", textDecoration: "none" }}>Meet Claire</a>
            <a href="#meet-charlotte" style={{ marginRight: 16, color: "#fff", textDecoration: "none" }}>Meet Charlotte</a>
            <a href="#brands" style={{ marginRight: 16, color: "#fff", textDecoration: "none" }}>Brands</a>
            <a href="#family" style={{ marginRight: 16, color: "#fff", textDecoration: "none" }}>Family</a>
            <a href="#contact" style={{ color: "#fff", textDecoration: "none" }}>Contact</a>
          </nav>
          <a href="#contact" style={buttonStyle}>Book Courtney</a>
        </div>
      </header>

      {/* HERO (split) */}
      <section id="home" style={{ position: "relative", overflow: "hidden" }}>
        <div style={{ position: "absolute", inset: 0, backgroundImage: "url('/assets/hero-cover.jpg')", backgroundSize: "cover", backgroundPosition: "center" }} />
        <div style={{ position: "absolute", inset: 0, background: "linear-gradient(to bottom, rgba(0,0,0,.7), rgba(123,31,162,.3), rgba(0,0,0,.9))" }} />
        <div style={{ position: "relative", zIndex: 1, maxWidth: 1120, margin: "0 auto", padding: "96px 24px", display: "grid", gap: 24 }}>
          <div>
            <div style={{ display: "inline-block", padding: "4px 12px", border: "1px solid rgba(255,255,255,.2)", borderRadius: 999, fontSize: 12, textTransform: "uppercase" }}>
              Strategic. Savage. Solution-Driven.
            </div>
            <h1 style={{ fontSize: "2.5em", fontWeight: 800, marginTop: 16 }}>I build empires from chaos. Louder. Brighter. Unstoppable.</h1>
            <p style={{ opacity: .9, maxWidth: 640 }}>
              I’m Courtney Devine — nurse, JD-in-progress, media creator, and entrepreneur. I weaponize truth, convert pain into power, and turn audiences into action.
            </p>
            <div style={{ marginTop: 24 }}>
              <a href="#contact" style={buttonStyle}>Partner with me →</a>
            </div>
          </div>
          <div style={{ textAlign: "right" }}>
            <Img src="/assets/courtney-portrait.jpg" alt="Courtney Devine portrait" style={{ maxWidth: 400, borderRadius: 24 }} />
          </div>
        </div>
      </section>

      {/* ABOUT */}
      <Section id="about">
        <h2 style={{ fontWeight: 800 }}>Meet Courtney — The Strategist, the Mother, the Fire</h2>
        <p style={{ marginTop: 16, opacity: .9 }}>
          Courtney Devine is a Registered Nurse (BSN) and DNP-PMHNP student, a JD candidate, and the founder of the Devine brand ecosystem. She builds businesses that protect, perform, and inspire—Devine Intervention™ (media & advocacy), Twirl & Dash™ (mother–daughter apparel), Devine Formula™ (performance nutrition), Devine Docket™ (newsletter), and Courtroom Angels™ (donor network). A survivor and mother to Claire (11) and Charlotte (4), Courtney turns chaos into strategy and truth into momentum.
        </p>
      </Section>

      {/* BRANDS */}
      <Section id="brands">
        <h2 style={{ textAlign: "center", fontWeight: 800 }}>The Devine Ecosystem</h2>
        <Grid>
          <Card>
            <Img src="/assets/placeholder.jpg" alt="Devine Intervention" />
            <h3 style={{ fontWeight: 700, margin: "8px 0" }}>Devine Intervention™</h3>
            <p style={{ opacity: .9 }}>A survivor-led media and advocacy platform empowering women to reclaim their voices and rewrite the narrative.</p>
          </Card>
          <Card>
            <Img src="/assets/placeholder.jpg" alt="Twirl & Dash" />
            <h3 style={{ fontWeight: 700, margin: "8px 0" }}>Twirl & Dash™</h3>
            <p style={{ opacity: .9 }}>Mother–daughter apparel co-created with Claire & Charlotte — made to move, play, and shine.</p>
          </Card>
          <Card>
            <Img src="/assets/placeholder.jpg" alt="Devine Formula" />
            <h3 style={{ fontWeight: 700, margin: "8px 0" }}>Devine Formula™</h3>
            <p style={{ opacity: .9 }}>Performance nutrition engineered for the relentless. Power. Precision. Performance.</p>
          </Card>
        </Grid>
      </Section>

      {/* FAMILY */}
      <Section id="family">
        <h2 style={{ textAlign: "center", fontWeight: 800 }}>The Devine Family — Heart, Hooves & Paws</h2>
        <Grid>
          <Card>
            <Img src="/assets/family/maple.jpg" alt="Maple" />
            <h3 style={{ fontWeight: 700, margin: "8px 0" }}>Maple — The Snuggle Bug</h3>
            <p style={{ opacity: .9 }}>Loyal, gentle, and happiest under a cozy blanket.</p>
          </Card>
          <Card>
            <Img src="/assets/family/moe.jpg" alt="Moe" />
            <h3 style={{ fontWeight: 700, margin: "8px 0" }}>Moe — The Tiny Jumper</h3>
            <p style={{ opacity: .9 }}>Energetic, playful, and always ready for new tricks.</p>
          </Card>
          <Card>
            <Img src="/assets/family/tucker.jpg" alt="Tucker" />
            <h3 style={{ fontWeight: 700, margin: "8px 0" }}>Tucker — The Protector</h3>
            <p style={{ opacity: .9 }}>Smart, snuggly, and steady. Quiet devotion, big heart.</p>
          </Card>
          <Card>
            <Img src="/assets/family/millie.jpg" alt="Millie" />
            <h3 style={{ fontWeight: 700, margin: "8px 0" }}>Millie — The Mini Muse</h3>
            <p style={{ opacity: .9 }}>Small body, big spirit, pure comic relief.</p>
          </Card>
          <Card>
            <Img src="/assets/family/bubbles.jpg" alt="Bubbles" />
            <h3 style={{ fontWeight: 700, margin: "8px 0" }}>Bubbles — The Grumpy King</h3>
            <p style={{ opacity: .9 }}>Demands pets, gives sass. Royal energy only.</p>
          </Card>
        </Grid>
      </Section>

      {/* CONTACT */}
      <Section id="contact">
        <h2 style={{ fontWeight: 800 }}>Book Courtney</h2>
        <p>Speaking, partnerships, media, or advisory. Serious inquiries only.</p>
        <form action="https://formspree.io/f/your-form-id" method="POST">
          <input name="name" placeholder="Your name" required style={{ display: "block", margin: "8px 0", padding: 10, width: "100%", borderRadius: 8 }} />
          <input type="email" name="email" placeholder="Your email" required style={{ display: "block", margin: "8px 0", padding: 10, width: "100%", borderRadius: 8 }} />
          <textarea name="message" placeholder="Tell me what you want to build together" style={{ display: "block", margin: "8px 0", padding: 10, width: "100%", borderRadius: 8, minHeight: 120 }} />
          <button type="submit" style={buttonStyle}>Submit</button>
        </form>
      </Section>

      {/* FOOTER */}
      <footer style={{ borderTop: "1px solid rgba(255,255,255,.1)", textAlign: "center", padding: "40px 0", fontSize: 14, opacity: .8 }}>
        <div>© {new Date().getFullYear()} Devine — All Rights Reserved.<br />Disclaimer: Courtney is not an attorney. All legal content is educational/advocacy only.</div>
      </footer>
    </div>
  );
}
