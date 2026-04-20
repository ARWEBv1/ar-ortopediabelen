<!doctype html>
<html lang="es">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Ortopediasbelen - Sublimados</title>
  <style>
    :root {
      --ink: #1d2528;
      --muted: #617074;
      --line: #d9e0df;
      --paper: #f7faf9;
      --panel: #ffffff;
      --green: #0f7c6d;
      --green-dark: #09594f;
      --coral: #d8563b;
      --yellow: #e2ad2f;
      --wall: #e8eeee;
      --floor: #b9a68a;
      --shadow: 0 16px 45px rgba(29, 37, 40, 0.16);
    }

    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      min-height: 100vh;
      color: var(--ink);
      font-family: Arial, Helvetica, sans-serif;
      background: var(--paper);
    }

    body.locked .app {
      display: none;
    }

    body.unlocked .auth-screen {
      display: none;
    }

    body.client-mode .admin-only {
      display: none;
    }

    button,
    input,
    select {
      font: inherit;
    }

    .app {
      min-height: 100vh;
      display: grid;
      grid-template-columns: minmax(320px, 420px) minmax(0, 1fr);
    }

    .auth-screen {
      min-height: 100vh;
      display: grid;
      place-items: center;
      padding: 22px;
      background:
        linear-gradient(180deg, rgba(255, 255, 255, 0.72), rgba(247, 250, 249, 0.96)),
        linear-gradient(135deg, #dfe9e8, #f7faf9 44%, #d9e0df);
    }

    .auth-panel {
      width: min(440px, 100%);
      background: #fff;
      border: 1px solid var(--line);
      border-radius: 8px;
      padding: 24px;
      box-shadow: var(--shadow);
    }

    .auth-panel h1 {
      margin-bottom: 6px;
    }

    .auth-form {
      display: grid;
      gap: 12px;
      margin-top: 20px;
    }

    .auth-tabs {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 8px;
      margin-top: 18px;
    }

    .auth-tab {
      border: 1px solid var(--line);
      border-radius: 8px;
      padding: 10px;
      background: #fff;
      cursor: pointer;
      font-weight: 700;
    }

    .auth-tab.is-active {
      color: #fff;
      border-color: var(--green);
      background: var(--green);
    }

    .auth-panel-block {
      display: none;
    }

    .auth-panel-block.is-active {
      display: block;
    }

    .field {
      display: grid;
      gap: 6px;
    }

    .field label {
      font-weight: 700;
      font-size: 14px;
    }

    .field input {
      width: 100%;
      border: 1px solid var(--line);
      border-radius: 8px;
      padding: 11px 12px;
      color: var(--ink);
      background: #fff;
    }

    .primary-action,
    .secondary-action {
      border: 1px solid var(--green);
      border-radius: 8px;
      padding: 11px 14px;
      cursor: pointer;
      font-weight: 700;
    }

    .primary-action {
      color: #fff;
      background: var(--green);
    }

    .secondary-action {
      color: var(--green-dark);
      background: #fff;
    }

    .full-action {
      width: 100%;
    }

    .auth-message {
      min-height: 20px;
      color: var(--coral);
      font-size: 14px;
      line-height: 1.35;
    }

    .account-actions {
      display: grid;
      gap: 10px;
    }

    .qr-box {
      display: grid;
      justify-items: start;
      gap: 10px;
      margin-top: 14px;
      padding: 12px;
      border: 1px solid var(--line);
      border-radius: 8px;
      background: #fbfdfd;
    }

    .qr-box img {
      width: 180px;
      height: 180px;
      border: 1px solid var(--line);
      border-radius: 8px;
      background: #fff;
    }

    .qr-link {
      width: 100%;
      overflow-wrap: anywhere;
      color: var(--muted);
      font-size: 13px;
      line-height: 1.35;
    }

    .controls {
      background: var(--panel);
      border-right: 1px solid var(--line);
      padding: 24px;
      overflow: auto;
    }

    h1 {
      margin: 0 0 8px;
      font-size: 30px;
      line-height: 1.1;
    }

    .intro {
      margin: 0 0 22px;
      color: var(--muted);
      line-height: 1.45;
    }

    .group {
      border-top: 1px solid var(--line);
      padding: 18px 0;
    }

    .group:first-of-type {
      border-top: 0;
      padding-top: 0;
    }

    .group-title {
      display: flex;
      align-items: baseline;
      justify-content: space-between;
      gap: 12px;
      margin-bottom: 12px;
      font-weight: 700;
    }

    .hint {
      color: var(--muted);
      font-size: 13px;
      font-weight: 400;
    }

    .choice-grid {
      display: grid;
      grid-template-columns: repeat(2, minmax(0, 1fr));
      gap: 10px;
    }

    .choice {
      border: 1px solid var(--line);
      background: #fff;
      border-radius: 8px;
      padding: 12px;
      cursor: pointer;
      text-align: left;
      min-height: 70px;
      transition: border-color 160ms ease, transform 160ms ease, box-shadow 160ms ease;
    }

    .choice:hover {
      transform: translateY(-1px);
      box-shadow: 0 8px 20px rgba(29, 37, 40, 0.09);
    }

    .choice.is-active {
      border-color: var(--green);
      box-shadow: inset 0 0 0 2px var(--green);
    }

    .choice strong {
      display: block;
      font-size: 18px;
      margin-bottom: 4px;
    }

    .choice span {
      color: var(--muted);
      font-size: 13px;
      line-height: 1.3;
    }

    .segmented {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 8px;
    }

    .segmented.no-four {
      grid-template-columns: repeat(2, 1fr);
    }

    .segment,
    .orientation {
      border: 1px solid var(--line);
      background: #fff;
      border-radius: 8px;
      padding: 11px 8px;
      cursor: pointer;
      font-weight: 700;
      text-align: center;
    }

    .segment.is-active,
    .orientation.is-active {
      color: #fff;
      border-color: var(--green);
      background: var(--green);
    }

    .orientation-row {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 8px;
      margin-top: 10px;
    }

    .segment.is-hidden {
      display: none;
    }

    .upload-box {
      border: 1px dashed #9aa9aa;
      border-radius: 8px;
      padding: 12px;
      background: #fbfdfd;
    }

    .upload-box label {
      display: block;
      margin-bottom: 8px;
      font-weight: 700;
    }

    .upload-box input {
      width: 100%;
    }

    .sample-grid {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 8px;
      margin-top: 12px;
    }

    .sample {
      position: relative;
      border: 2px solid transparent;
      border-radius: 8px;
      padding: 0;
      overflow: hidden;
      background: #fff;
      cursor: pointer;
      aspect-ratio: 1;
    }

    .sample img {
      width: 100%;
      height: 100%;
      display: block;
      object-fit: cover;
    }

    .sample.is-active {
      border-color: var(--coral);
    }

    .summary {
      display: grid;
      gap: 8px;
      color: var(--muted);
      font-size: 14px;
      line-height: 1.35;
    }

    .summary strong {
      color: var(--ink);
    }

    .price-line {
      display: inline-flex;
      align-items: center;
      justify-content: space-between;
      gap: 12px;
      padding: 12px;
      border: 1px solid var(--line);
      border-radius: 8px;
      background: #fbfdfd;
      color: var(--ink);
      font-weight: 700;
    }

    .price-line span:last-child {
      color: var(--coral);
      font-size: 20px;
    }

    .stage {
      min-height: 100vh;
      display: grid;
      grid-template-rows: auto minmax(520px, 1fr);
      background:
        linear-gradient(180deg, rgba(238, 244, 243, 0.72), rgba(216, 226, 223, 0.72)),
        url("https://images.unsplash.com/photo-1586023492125-27b2c045efd7?auto=format&fit=crop&w=1600&q=80") center / cover no-repeat;
    }

    .topbar {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 16px;
      padding: 18px 24px;
      background: rgba(255, 255, 255, 0.7);
      border-bottom: 1px solid rgba(29, 37, 40, 0.08);
      backdrop-filter: blur(10px);
    }

    .topbar strong {
      font-size: 18px;
    }

    .topbar span {
      color: var(--muted);
      font-size: 14px;
    }

    .view-actions {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      justify-content: flex-end;
    }

    .view-button {
      border: 1px solid var(--line);
      border-radius: 8px;
      padding: 9px 11px;
      background: #fff;
      cursor: pointer;
      font-weight: 700;
    }

    .view-button.is-active {
      color: #fff;
      border-color: var(--green);
      background: var(--green);
    }

    .room {
      position: relative;
      min-height: 520px;
      overflow: hidden;
      display: flex;
      align-items: center;
      justify-content: center;
      padding: 34px 24px 180px;
    }

    .room.view-3d .gallery,
    .room.view-3d .sofa,
    .room.view-3d .lamp {
      display: none;
    }

    .room::before {
      content: "";
      position: absolute;
      left: 0;
      right: 0;
      top: 0;
      bottom: 0;
      background: linear-gradient(180deg, rgba(255, 255, 255, 0.18), rgba(29, 37, 40, 0.12));
      pointer-events: none;
    }

    .sofa,
    .lamp {
      display: none;
    }

    .sofa {
      position: absolute;
      left: 50%;
      bottom: 60px;
      width: min(620px, 78vw);
      height: 118px;
      transform: translateX(-50%);
      background: #2f7d73;
      border-radius: 8px 8px 14px 14px;
      box-shadow: var(--shadow);
    }

    .sofa::before,
    .sofa::after {
      content: "";
      position: absolute;
      bottom: 22px;
      width: 110px;
      height: 88px;
      background: #276b63;
      border-radius: 8px;
    }

    .sofa::before {
      left: -42px;
    }

    .sofa::after {
      right: -42px;
    }

    .cushion {
      position: absolute;
      top: -28px;
      width: 72px;
      height: 72px;
      border-radius: 8px;
      background: var(--yellow);
      box-shadow: 0 8px 16px rgba(29, 37, 40, 0.12);
    }

    .cushion.one {
      left: 22%;
    }

    .cushion.two {
      right: 22%;
      background: var(--coral);
    }

    .lamp {
      position: absolute;
      right: clamp(18px, 8vw, 110px);
      bottom: 72px;
      width: 70px;
      height: 250px;
      border-bottom: 12px solid #555f60;
    }

    .lamp::before {
      content: "";
      position: absolute;
      left: 32px;
      top: 70px;
      width: 6px;
      height: 170px;
      background: #555f60;
    }

    .lamp::after {
      content: "";
      position: absolute;
      left: 0;
      top: 0;
      width: 70px;
      height: 56px;
      background: #f2f6f5;
      border: 1px solid #cfd8d7;
      border-radius: 8px 8px 4px 4px;
      box-shadow: 0 16px 25px rgba(255, 255, 255, 0.55);
    }

    .gallery {
      position: relative;
      z-index: 2;
      display: grid;
      gap: var(--gap, 14px);
      align-items: center;
      justify-items: center;
      filter: drop-shadow(0 18px 18px rgba(29, 37, 40, 0.16));
      margin-top: -80px;
    }

    .gallery.layout-1 {
      grid-template-columns: 1fr;
    }

    .gallery.layout-2 {
      grid-template-columns: repeat(2, 1fr);
    }

    .gallery.layout-2.split-horizontal {
      grid-template-columns: 1fr;
    }

    .gallery.layout-4 {
      grid-template-columns: repeat(2, 1fr);
      gap: 10px;
    }

    .frame {
      width: var(--frame-w, 180px);
      height: var(--frame-h, 240px);
      border: 8px solid #1d2528;
      background: #fff;
      box-shadow: inset 0 0 0 5px #fff, 0 8px 18px rgba(29, 37, 40, 0.18);
      overflow: hidden;
    }

    .art {
      width: 100%;
      height: 100%;
      background-image: var(--art);
      background-position: center;
      background-size: cover;
      background-repeat: no-repeat;
    }

    .layout-4 .art {
      background-size: 200% 200%;
    }

    .split-vertical .art {
      background-size: 200% 100%;
    }

    .split-horizontal .art {
      background-size: 100% 200%;
    }

    .split-vertical .piece-1 .art {
      background-position: left center;
    }

    .split-vertical .piece-2 .art {
      background-position: right center;
    }

    .split-horizontal .piece-1 .art {
      background-position: center top;
    }

    .split-horizontal .piece-2 .art {
      background-position: center bottom;
    }

    .layout-4 .piece-1 .art {
      background-position: left top;
    }

    .layout-4 .piece-2 .art {
      background-position: right top;
    }

    .layout-4 .piece-3 .art {
      background-position: left bottom;
    }

    .layout-4 .piece-4 .art {
      background-position: right bottom;
    }

    .piece-label {
      position: absolute;
      width: 1px;
      height: 1px;
      overflow: hidden;
      clip: rect(0 0 0 0);
    }

    .note {
      position: absolute;
      z-index: 4;
      left: 24px;
      bottom: 22px;
      max-width: 380px;
      padding: 12px 14px;
      border-radius: 8px;
      background: rgba(255, 255, 255, 0.86);
      color: var(--muted);
      font-size: 14px;
      line-height: 1.4;
      box-shadow: 0 8px 24px rgba(29, 37, 40, 0.12);
    }

    .product3d {
      position: relative;
      z-index: 3;
      display: none;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      gap: 18px;
      width: min(680px, 90vw);
      min-height: 380px;
      margin-top: -70px;
      perspective: 1000px;
    }

    .room.view-3d .product3d {
      display: flex;
    }

    .slab {
      position: relative;
      width: var(--model-w, 220px);
      height: var(--model-h, 300px);
      transform-style: preserve-3d;
      transform: rotateX(var(--rotate-x, 8deg)) rotateY(var(--rotate-y, -28deg)) rotateZ(var(--rotate-z, 0deg));
      transition: transform 260ms ease;
    }

    .model-face {
      position: absolute;
      inset: 0;
      border: 8px solid #1d2528;
      border-radius: 6px;
      overflow: hidden;
      backface-visibility: hidden;
      box-shadow: 0 24px 44px rgba(29, 37, 40, 0.24);
    }

    .model-front {
      background-image: var(--art);
      background-size: cover;
      background-position: center;
      transform: translateZ(14px);
    }

    .model-back {
      display: grid;
      place-items: center;
      padding: 16px;
      color: #4f595b;
      text-align: center;
      font-weight: 700;
      background:
        linear-gradient(135deg, rgba(255,255,255,0.72), rgba(130,141,144,0.2) 38%, rgba(255,255,255,0.42) 39%, rgba(102,113,116,0.2) 70%),
        repeating-linear-gradient(90deg, rgba(255,255,255,0.28) 0 2px, rgba(83,92,94,0.08) 2px 7px),
        #c4ccce;
      transform: rotateY(180deg) translateZ(14px);
    }

    .model-side {
      position: absolute;
      top: 8px;
      right: -14px;
      width: 28px;
      height: calc(100% - 16px);
      border-radius: 0 6px 6px 0;
      background: linear-gradient(90deg, #9aa4a6, #e4e9e9 48%, #737f82);
      transform: rotateY(90deg) translateZ(calc(var(--model-w, 220px) - 14px));
      transform-origin: left center;
    }

    .model-controls {
      width: min(460px, 100%);
      display: grid;
      gap: 10px;
      padding: 12px;
      border: 1px solid rgba(255, 255, 255, 0.72);
      border-radius: 8px;
      background: rgba(255, 255, 255, 0.84);
      box-shadow: 0 10px 28px rgba(29, 37, 40, 0.14);
    }

    .model-control {
      display: grid;
      grid-template-columns: 72px 1fr;
      align-items: center;
      gap: 10px;
      color: var(--ink);
      font-size: 14px;
      font-weight: 700;
    }

    .model-control input {
      width: 100%;
    }

    .legal-footer {
      padding: 16px 24px;
      border-top: 1px solid var(--line);
      background: #fff;
      color: var(--muted);
      text-align: center;
      font-size: 13px;
      line-height: 1.4;
    }

    @media (max-width: 900px) {
      .app {
        grid-template-columns: 1fr;
      }

      .controls {
        border-right: 0;
        border-bottom: 1px solid var(--line);
      }

      .stage {
        min-height: 720px;
        grid-template-rows: auto 1fr;
      }

      .room {
        min-height: 640px;
        padding-bottom: 170px;
      }
    }

    @media (max-width: 520px) {
      .controls {
        padding: 18px;
      }

      h1 {
        font-size: 26px;
      }

      .choice-grid {
        grid-template-columns: 1fr;
      }

      .topbar {
        align-items: flex-start;
        flex-direction: column;
        padding: 16px 18px;
      }

      .room {
        padding: 22px 12px 160px;
      }

      .sofa {
        width: 74vw;
        height: 96px;
      }

      .sofa::before,
      .sofa::after {
        width: 72px;
      }

      .lamp {
        display: none;
      }

      .gallery {
        margin-top: -90px;
      }

      .frame {
        border-width: 6px;
      }

      .note {
        left: 12px;
        right: 12px;
        bottom: 12px;
        max-width: none;
      }
    }
  </style>
</head>
<body class="locked">
  <section class="auth-screen" aria-label="Acceso privado">
    <div class="auth-panel">
      <h1>Ortopediasbelen - Sublimados</h1>
      <p class="intro">Acceso privado al simulador de cuadros.</p>
      <div class="auth-tabs" id="authTabs">
        <button class="auth-tab is-active" type="button" data-panel="clientPanel">Cliente</button>
        <button class="auth-tab" type="button" data-panel="adminPanel">Administrador</button>
      </div>

      <div class="auth-panel-block is-active" id="clientPanel">
        <form class="auth-form" id="clientLoginForm">
          <div class="field">
            <label for="clientPassword">Contrasena de cliente</label>
            <input id="clientPassword" type="password" autocomplete="current-password">
          </div>
          <button class="primary-action" type="submit">Abrir simulador</button>
          <div class="auth-message" id="clientLoginMessage"></div>
        </form>
      </div>

      <div class="auth-panel-block" id="adminPanel">
        <form class="auth-form" id="adminLoginForm">
          <input id="adminEmail" type="hidden" value="yuki053@gmail.com">
          <div class="field">
            <label for="adminPassword">Contrasena de administrador</label>
            <input id="adminPassword" type="password" autocomplete="current-password">
          </div>
          <button class="primary-action" type="submit">Entrar como administrador</button>
          <div class="auth-message" id="adminLoginMessage"></div>
        </form>
      </div>

      <div class="auth-panel-block" id="setupPanel"></div>
    </div>
  </section>

  <main class="app">
    <section class="controls" aria-label="Opciones del simulador">
      <h1>Ortopediasbelen - Sublimados</h1>
      <p class="intro">Elige el formato, la cantidad y carga tus imagenes. La vista calcula la proporcion para mostrar como se veria en un living.</p>

      <div class="group">
        <div class="group-title">
          <span>Formato</span>
          <span class="hint">centimetros</span>
        </div>
        <div class="choice-grid" id="formatChoices">
          <button class="choice is-active" type="button" data-width="20" data-height="30">
            <strong>20 x 30</strong>
            <span>Ideal para composiciones pequenas.</span>
          </button>
          <button class="choice" type="button" data-width="30" data-height="40">
            <strong>30 x 40</strong>
            <span>Mas presencia sin ocupar tanto muro.</span>
          </button>
          <button class="choice" type="button" data-width="30" data-height="60">
            <strong>30 x 60</strong>
            <span>Puede ir vertical u horizontal.</span>
          </button>
          <button class="choice" type="button" data-width="40" data-height="60">
            <strong>40 x 60</strong>
            <span>Formato grande para una imagen protagonista.</span>
          </button>
        </div>
        <div class="orientation-row" id="orientationRow">
          <button class="orientation is-active" type="button" data-orientation="vertical">Vertical</button>
          <button class="orientation" type="button" data-orientation="horizontal">Horizontal</button>
        </div>
      </div>

      <div class="group">
        <div class="group-title">
          <span>Cantidad</span>
          <span class="hint" id="quantityHint">x1, x2 o x4</span>
        </div>
        <div class="segmented" id="quantityChoices">
          <button class="segment is-active" type="button" data-count="1">x1</button>
          <button class="segment" type="button" data-count="2">x2</button>
          <button class="segment" type="button" data-count="4" id="countFour">x4</button>
        </div>
      </div>

      <div class="group">
        <div class="group-title">
          <span>Imagenes</span>
          <span class="hint" id="uploadHint">sube 1 imagen</span>
        </div>
        <div class="upload-box">
          <label for="imageUpload" id="uploadLabel">Imagen para el cuadro</label>
          <input id="imageUpload" type="file" accept="image/*" multiple name="attachment" form="orderForm">
        </div>
        <div class="sample-grid" aria-label="Imagenes de ejemplo">
          <button class="sample is-active" type="button" data-sample="https://images.unsplash.com/photo-1448375240586-882707db888b?auto=format&fit=crop&w=1200&q=80">
            <img alt="Bosque" src="https://images.unsplash.com/photo-1448375240586-882707db888b?auto=format&fit=crop&w=1200&q=80">
          </button>
          <button class="sample" type="button" data-sample="https://images.unsplash.com/photo-1507525428034-b723cf961d3e?auto=format&fit=crop&w=1200&q=80">
            <img alt="Playa" src="https://images.unsplash.com/photo-1507525428034-b723cf961d3e?auto=format&fit=crop&w=1200&q=80">
          </button>
          <button class="sample" type="button" data-sample="https://images.unsplash.com/photo-1500530855697-b586d89ba3ee?auto=format&fit=crop&w=1200&q=80">
            <img alt="Montana" src="https://images.unsplash.com/photo-1500530855697-b586d89ba3ee?auto=format&fit=crop&w=1200&q=80">
          </button>
          <button class="sample" type="button" data-sample="https://images.unsplash.com/photo-1416879595882-3373a0480b5b?auto=format&fit=crop&w=1200&q=80">
            <img alt="Jardin" src="https://images.unsplash.com/photo-1416879595882-3373a0480b5b?auto=format&fit=crop&w=1200&q=80">
          </button>
        </div>
      </div>

      <div class="group">
        <div class="group-title">
          <span>Pedido actual</span>
        </div>
        <div class="summary">
          <div><strong id="summaryTitle">20 x 30 x1</strong></div>
          <div id="summaryText">1 cuadro individual de 20 x 30 cm.</div>
          <div id="summaryTotal">Tamano visual total: 20 x 30 cm.</div>
          <div class="price-line">
            <span>Precio</span>
            <span id="summaryPrice">$20.000</span>
          </div>
          <button class="primary-action full-action" id="sendOrderButton" type="button">Enviar pedido</button>
          <div class="hint" id="sendHint">Se enviara el pedido con la imagen subida a admin@ortopediasbelen.com.</div>
        </div>
      </div>

      <div class="group admin-only">
        <div class="group-title">
          <span>Administrador</span>
          <span class="hint">cliente y QR</span>
        </div>
        <form class="auth-form" id="changeClientPasswordForm">
          <div class="field">
            <label for="adminCurrentPassword">Contrasena de administrador</label>
            <input id="adminCurrentPassword" type="password" autocomplete="current-password">
          </div>
          <div class="field">
            <label for="newClientPassword">Nueva contrasena para clientes</label>
            <input id="newClientPassword" type="password" autocomplete="new-password">
          </div>
          <button class="primary-action" type="submit">Cambiar clave cliente</button>
          <button class="secondary-action" id="logoutButton" type="button">Cerrar sesion</button>
          <div class="auth-message" id="clientPasswordMessage"></div>
        </form>
        <div class="qr-box">
          <strong>QR para clientes</strong>
          <img id="clientQr" alt="QR de acceso cliente">
          <div class="qr-link" id="clientQrLink"></div>
        </div>
      </div>
    </section>

    <section class="stage" aria-label="Vista previa en living">
      <div class="topbar">
        <div>
          <strong id="previewTitle">20 x 30 x1</strong>
          <span id="previewMode">Un cuadro con una imagen.</span>
        </div>
        <div class="view-actions">
          <button class="view-button is-active" id="livingViewButton" type="button">Living</button>
          <button class="view-button" id="modelViewButton" type="button">3D</button>
          <button class="view-button" id="flipModelButton" type="button">Ver aluminio</button>
        </div>
      </div>
      <div class="room" id="room">
        <div class="gallery layout-1" id="gallery" aria-live="polite"></div>
        <div class="product3d" id="product3d" aria-label="Vista 3D del cuadro">
          <div class="slab" id="modelSlab">
            <div class="model-face model-front" id="modelFront"></div>
            <div class="model-face model-back">Reverso aluminio</div>
            <div class="model-side" aria-hidden="true"></div>
          </div>
          <div class="model-controls">
            <label class="model-control" for="rotateX">
              <span>Arriba</span>
              <input id="rotateX" type="range" min="-70" max="70" value="8">
            </label>
            <label class="model-control" for="rotateY">
              <span>Lados</span>
              <input id="rotateY" type="range" min="-180" max="180" value="-28">
            </label>
            <label class="model-control" for="rotateZ">
              <span>Giro</span>
              <input id="rotateZ" type="range" min="-45" max="45" value="0">
            </label>
            <button class="secondary-action" id="resetModelButton" type="button">Centrar 3D</button>
          </div>
        </div>
        <div class="sofa" aria-hidden="true">
          <span class="cushion one"></span>
          <span class="cushion two"></span>
        </div>
        <div class="lamp" aria-hidden="true"></div>
        <div class="note" id="note">En x4 se usa una sola imagen grande y se divide en cuatro cuadros iguales.</div>
      </div>
    </section>
  </main>

  <footer class="legal-footer">Ante copia o plagio, la demanda le llega. Propiedad de Ortopediasbelen.</footer>

  <form id="orderForm" action="https://formsubmit.co/admin@ortopediasbelen.com" method="POST" enctype="multipart/form-data">
    <input type="hidden" name="_subject" id="orderSubject">
    <input type="hidden" name="pedido" id="orderMessage">
    <input type="hidden" name="_captcha" value="false">
    <input type="hidden" name="_template" value="table">
  </form>

  <script>
    const state = {
      width: 20,
      height: 30,
      count: 1,
      orientation: "vertical",
      images: ["https://images.unsplash.com/photo-1448375240586-882707db888b?auto=format&fit=crop&w=1200&q=80"],
      view: "living",
      modelSide: "front",
      rotateX: 8,
      rotateY: -28,
      rotateZ: 0,
      imageNames: ["Imagen de ejemplo"],
    };

    const prices = {
      "20x30": { 1: 20000, 2: 25000, 4: 60000 },
      "30x40": { 1: 25000, 2: 40000, 4: 75000 },
      "30x60": { 1: 30000, 2: 50000 },
      "40x60": { 1: 60000, 2: 100000, 4: 200000 },
    };

    const ADMIN_EMAIL = "yuki053@gmail.com";
    const ADMIN_PASSWORD_CODE = "a9461750";
    const CLIENT_PASSWORD_KEY = "ortopediasbelenClientPasswordHash";
    const SESSION_KEY = "ortopediasbelenSessionMode";

    const authTabs = document.getElementById("authTabs");
    const clientPanel = document.getElementById("clientPanel");
    const adminPanel = document.getElementById("adminPanel");
    const setupPanel = document.getElementById("setupPanel");
    const clientLoginForm = document.getElementById("clientLoginForm");
    const adminLoginForm = document.getElementById("adminLoginForm");
    const adminEmail = document.getElementById("adminEmail");
    const clientPassword = document.getElementById("clientPassword");
    const adminPassword = document.getElementById("adminPassword");
    const clientLoginMessage = document.getElementById("clientLoginMessage");
    const adminLoginMessage = document.getElementById("adminLoginMessage");
    const changeClientPasswordForm = document.getElementById("changeClientPasswordForm");
    const adminCurrentPassword = document.getElementById("adminCurrentPassword");
    const newClientPassword = document.getElementById("newClientPassword");
    const clientPasswordMessage = document.getElementById("clientPasswordMessage");
    const clientQr = document.getElementById("clientQr");
    const clientQrLink = document.getElementById("clientQrLink");
    const logoutButton = document.getElementById("logoutButton");
    const formatChoices = document.getElementById("formatChoices");
    const quantityChoices = document.getElementById("quantityChoices");
    const orientationRow = document.getElementById("orientationRow");
    const countFour = document.getElementById("countFour");
    const quantityHint = document.getElementById("quantityHint");
    const gallery = document.getElementById("gallery");
    const upload = document.getElementById("imageUpload");
    const uploadHint = document.getElementById("uploadHint");
    const uploadLabel = document.getElementById("uploadLabel");
    const previewTitle = document.getElementById("previewTitle");
    const previewMode = document.getElementById("previewMode");
    const summaryTitle = document.getElementById("summaryTitle");
    const summaryText = document.getElementById("summaryText");
    const summaryTotal = document.getElementById("summaryTotal");
    const summaryPrice = document.getElementById("summaryPrice");
    const note = document.getElementById("note");
    const room = document.getElementById("room");
    const product3d = document.getElementById("product3d");
    const modelSlab = document.getElementById("modelSlab");
    const modelFront = document.getElementById("modelFront");
    const livingViewButton = document.getElementById("livingViewButton");
    const modelViewButton = document.getElementById("modelViewButton");
    const flipModelButton = document.getElementById("flipModelButton");
    const rotateX = document.getElementById("rotateX");
    const rotateY = document.getElementById("rotateY");
    const rotateZ = document.getElementById("rotateZ");
    const resetModelButton = document.getElementById("resetModelButton");
    const sendOrderButton = document.getElementById("sendOrderButton");
    const sendHint = document.getElementById("sendHint");
    const orderForm = document.getElementById("orderForm");
    const orderSubject = document.getElementById("orderSubject");
    const orderMessage = document.getElementById("orderMessage");

    function setActive(container, selector, target) {
      container.querySelectorAll(selector).forEach((item) => item.classList.remove("is-active"));
      target.classList.add("is-active");
    }

    async function passwordHash(value) {
      let hash = 2166136261;
      const salted = `ortopediasbelen:${value}`;

      for (let i = 0; i < salted.length; i += 1) {
        hash ^= salted.charCodeAt(i);
        hash = Math.imul(hash, 16777619);
      }

      return (hash >>> 0).toString(16).padStart(8, "0");
    }

    async function passwordMatches(value, key) {
      return await passwordHash(value) === localStorage.getItem(key);
    }

    async function adminPasswordMatches(value) {
      return await passwordHash(value) === ADMIN_PASSWORD_CODE;
    }

    function hasClientPassword() {
      return Boolean(clientPasswordCode());
    }

    function showAuthPanel(panelId) {
      [clientPanel, adminPanel, setupPanel].forEach((panel) => {
        panel.classList.toggle("is-active", panel.id === panelId);
      });

      authTabs.querySelectorAll(".auth-tab").forEach((button) => {
        button.classList.toggle("is-active", button.dataset.panel === panelId);
      });
    }

    function setAccess(mode) {
      const unlocked = mode === "admin" || mode === "client";
      document.body.classList.toggle("unlocked", unlocked);
      document.body.classList.toggle("locked", !unlocked);
      document.body.classList.toggle("admin-mode", mode === "admin");
      document.body.classList.toggle("client-mode", mode === "client");
      updateClientQr();
    }

    function sessionMode() {
      return sessionStorage.getItem(SESSION_KEY);
    }

    function clientAccessUrl() {
      const cleanUrl = `${location.origin}${location.pathname}`;
      const code = localStorage.getItem(CLIENT_PASSWORD_KEY) || "";
      return `${cleanUrl}#cliente/${code}`;
    }

    function clientPasswordCode() {
      const match = location.hash.match(/^#cliente\/([a-f0-9]+)$/i);
      return match ? match[1] : localStorage.getItem(CLIENT_PASSWORD_KEY);
    }

    function updateClientQr() {
      const url = clientAccessUrl();
      clientQr.src = `https://api.qrserver.com/v1/create-qr-code/?size=220x220&data=${encodeURIComponent(url)}`;
      clientQrLink.textContent = url;
    }

    function effectiveSize() {
      return state.orientation === "horizontal"
        ? { width: state.height, height: state.width }
        : { width: state.width, height: state.height };
    }

    function isThirtySixty() {
      return state.width === 30 && state.height === 60;
    }

    function formatKey() {
      return `${state.width}x${state.height}`;
    }

    function currentPrice() {
      return prices[formatKey()][state.count];
    }

    function money(value) {
      return `$${value.toLocaleString("es-CL")}`;
    }

    function orderTitle() {
      const size = displaySize();
      return `${size.width}x${size.height} x${state.count} ${state.orientation}`;
    }

    function imageInstructions() {
      if (isSplitDiptych()) {
        return "Enviar 1 imagen cuadrada para dividir en dos cuadros 30x60.";
      }

      if (state.count === 2) {
        return "Enviar 2 imagenes distintas.";
      }

      if (state.count === 4) {
        return "Enviar 1 imagen para dividir en 4 cuadros.";
      }

      return "Enviar 1 imagen.";
    }

    function sendOrder() {
      if (!upload.files.length) {
        sendHint.textContent = "Sube la imagen del cliente antes de enviar el pedido.";
        upload.focus();
        return;
      }

      const subject = `Pedido ${orderTitle()} - Ortopediasbelen`;
      const body = [
        `Formato: ${orderTitle()}`,
        `Precio: ${money(currentPrice())}`,
        `Indicacion: ${imageInstructions()}`,
        `Imagen adjunta: ${state.imageNames.join(", ")}`,
        "Cliente enviado desde el simulador Ortopediasbelen.",
      ].join("\n");

      orderSubject.value = subject;
      orderMessage.value = body;
      sendHint.textContent = "Enviando pedido con imagen adjunta...";
      orderForm.submit();
    }

    function isSplitDiptych() {
      return isThirtySixty() && state.count === 2;
    }

    function displaySize() {
      if (isSplitDiptych()) {
        return { width: 30, height: 60 };
      }

      return effectiveSize();
    }

    function frameSize() {
      if (!isSplitDiptych()) {
        return effectiveSize();
      }

      return state.orientation === "horizontal"
        ? { width: 60, height: 30 }
        : { width: 30, height: 60 };
    }

    function totalSize(size) {
      if (isSplitDiptych()) {
        return { width: 60, height: 60 };
      }

      if (state.count === 4) {
        return { width: size.width * 2, height: size.height * 2 };
      }

      if (state.count === 2) {
        return { width: (size.width * 2) + 6, height: size.height };
      }

      return size;
    }

    function imageFor(index) {
      if (state.count === 2 && !isSplitDiptych()) {
        return state.images[index] || state.images[0];
      }

      return state.images[0];
    }

    function syncQuantityOptions() {
      countFour.classList.toggle("is-hidden", isThirtySixty());
      quantityChoices.classList.toggle("no-four", isThirtySixty());
      quantityHint.textContent = isThirtySixty() ? "x1 o x2" : "x1, x2 o x4";

      if (isThirtySixty() && state.count === 4) {
        state.count = 2;
        quantityChoices.querySelectorAll(".segment").forEach((item) => {
          item.classList.toggle("is-active", item.dataset.count === "2");
        });
      }
    }

    function renderFrames() {
      syncQuantityOptions();
      const size = frameSize();
      const total = totalSize(size);
      const maxWidth = window.innerWidth <= 520 ? 280 : window.innerWidth <= 900 ? 460 : 620;
      const maxHeight = window.innerWidth <= 520 ? 280 : 360;
      const scale = Math.min(maxWidth / total.width, maxHeight / total.height);
      const frameWidth = Math.max(70, Math.round(size.width * scale));
      const frameHeight = Math.max(90, Math.round(size.height * scale));

      const splitClass = isSplitDiptych() ? ` split-${state.orientation}` : "";
      gallery.className = `gallery layout-${state.count}${splitClass}`;
      gallery.style.setProperty("--frame-w", `${frameWidth}px`);
      gallery.style.setProperty("--frame-h", `${frameHeight}px`);
      gallery.innerHTML = "";

      for (let i = 0; i < state.count; i += 1) {
        const frame = document.createElement("div");
        frame.className = `frame piece-${i + 1}`;
        frame.style.setProperty("--art", `url("${imageFor(i)}")`);

        const art = document.createElement("div");
        art.className = "art";

        const label = document.createElement("span");
        label.className = "piece-label";
        label.textContent = `Cuadro ${i + 1}`;

        frame.append(art, label);
        gallery.appendChild(frame);
      }
    }

    function render3D() {
      const size = frameSize();
      const maxWidth = window.innerWidth <= 520 ? 230 : 320;
      const maxHeight = window.innerWidth <= 520 ? 300 : 390;
      const scale = Math.min(maxWidth / size.width, maxHeight / size.height);
      const modelWidth = Math.max(120, Math.round(size.width * scale));
      const modelHeight = Math.max(150, Math.round(size.height * scale));

      room.classList.toggle("view-3d", state.view === "3d");
      livingViewButton.classList.toggle("is-active", state.view === "living");
      modelViewButton.classList.toggle("is-active", state.view === "3d");
      flipModelButton.style.display = state.view === "3d" ? "" : "none";
      flipModelButton.textContent = Math.abs(state.rotateY) > 100 ? "Ver imagen" : "Ver aluminio";

      product3d.style.setProperty("--art", `url("${imageFor(0)}")`);
      product3d.style.setProperty("--model-w", `${modelWidth}px`);
      product3d.style.setProperty("--model-h", `${modelHeight}px`);
      modelSlab.style.setProperty("--model-w", `${modelWidth}px`);
      modelSlab.style.setProperty("--rotate-x", `${state.rotateX}deg`);
      modelSlab.style.setProperty("--rotate-y", `${state.rotateY}deg`);
      modelSlab.style.setProperty("--rotate-z", `${state.rotateZ}deg`);
      modelFront.style.backgroundImage = `url("${imageFor(0)}")`;
      rotateX.value = state.rotateX;
      rotateY.value = state.rotateY;
      rotateZ.value = state.rotateZ;
    }

    function renderText() {
      syncQuantityOptions();
      const size = displaySize();
      const total = totalSize(frameSize());
      const orientationText = ` ${state.orientation}`;
      const title = `${size.width} x ${size.height} x${state.count}`;

      let mode = `1 cuadro individual de ${size.width} x ${size.height} cm.`;
      let preview = "Un cuadro con una imagen.";
      let helper = "Sube 1 imagen";
      let label = "Imagen para el cuadro";

      if (state.count === 2) {
        mode = `2 cuadros de ${size.width} x ${size.height} cm con imagenes distintas.`;
        preview = "Dos cuadros, ideal para subir dos imagenes distintas.";
        helper = "sube 2 imagenes";
        label = "Imagenes para los dos cuadros";
      }

      if (isSplitDiptych()) {
        mode = state.orientation === "horizontal"
          ? "Formato elegido 30 x 60 x2. Una imagen de 60 x 60 cm se divide horizontalmente en dos mitades."
          : "Formato elegido 30 x 60 x2. Una imagen de 60 x 60 cm se divide verticalmente en dos mitades.";
        preview = "Una imagen de 60 x 60 cm dividida en dos cuadros.";
        helper = "sube 1 imagen";
        label = "Imagen 60 x 60 para dividir en dos";
      }

      if (state.count === 4) {
        mode = `4 cuadros de ${size.width} x ${size.height} cm. Una misma imagen queda dividida en 4 partes.`;
        preview = "Una imagen grande dividida en cuatro cuadros.";
        helper = "sube 1 imagen";
        label = "Imagen principal para dividir en cuatro";
      }

      previewTitle.textContent = `${title}${orientationText}`;
      previewMode.textContent = preview;
      summaryTitle.textContent = `${title}${orientationText}`;
      summaryText.textContent = mode;
      summaryTotal.textContent = `Tamano visual total: ${total.width} x ${total.height} cm.`;
      summaryPrice.textContent = money(currentPrice());
      uploadHint.textContent = helper;
      uploadLabel.textContent = label;
      note.textContent = isSplitDiptych()
        ? "En 30 x 60 x2 se usa una sola imagen de 60 x 60 cm y se parte en dos segun la direccion elegida."
        : state.count === 4
        ? "En x4 se usa una sola imagen grande y se divide en cuatro cuadros iguales."
        : "La proporcion respeta el formato elegido para que se entienda el tamano sobre el muro.";
    }

    function render() {
      renderFrames();
      render3D();
      renderText();
    }

    formatChoices.addEventListener("click", (event) => {
      const button = event.target.closest(".choice");
      if (!button) return;

      setActive(formatChoices, ".choice", button);
      state.width = Number(button.dataset.width);
      state.height = Number(button.dataset.height);

      render();
    });

    quantityChoices.addEventListener("click", (event) => {
      const button = event.target.closest(".segment");
      if (!button) return;

      setActive(quantityChoices, ".segment", button);
      state.count = Number(button.dataset.count);
      render();
    });

    orientationRow.addEventListener("click", (event) => {
      const button = event.target.closest(".orientation");
      if (!button) return;

      setActive(orientationRow, ".orientation", button);
      state.orientation = button.dataset.orientation;
      render();
    });

    livingViewButton.addEventListener("click", () => {
      state.view = "living";
      render();
    });

    modelViewButton.addEventListener("click", () => {
      state.view = "3d";
      render();
    });

    flipModelButton.addEventListener("click", () => {
      state.rotateY = Math.abs(state.rotateY) > 100 ? -28 : 180;
      state.view = "3d";
      render();
    });

    rotateX.addEventListener("input", () => {
      state.rotateX = Number(rotateX.value);
      state.view = "3d";
      render3D();
    });

    rotateY.addEventListener("input", () => {
      state.rotateY = Number(rotateY.value);
      state.view = "3d";
      render3D();
    });

    rotateZ.addEventListener("input", () => {
      state.rotateZ = Number(rotateZ.value);
      state.view = "3d";
      render3D();
    });

    resetModelButton.addEventListener("click", () => {
      state.rotateX = 8;
      state.rotateY = -28;
      state.rotateZ = 0;
      state.view = "3d";
      render();
    });

    sendOrderButton.addEventListener("click", sendOrder);

    document.querySelectorAll(".sample").forEach((button) => {
      button.addEventListener("click", () => {
        document.querySelectorAll(".sample").forEach((item) => item.classList.remove("is-active"));
        button.classList.add("is-active");
        state.images = [button.dataset.sample];
        state.imageNames = [button.querySelector("img").alt];
        upload.value = "";
        render();
      });
    });

    upload.addEventListener("change", () => {
      const maxFiles = state.count === 2 && !isSplitDiptych() ? 2 : 1;
      const files = Array.from(upload.files || []).slice(0, maxFiles);
      if (!files.length) return;

      Promise.all(files.map((file) => new Promise((resolve) => {
        const reader = new FileReader();
        reader.onload = () => resolve(reader.result);
        reader.readAsDataURL(file);
      }))).then((images) => {
        state.images = images;
        state.imageNames = files.map((file) => file.name);
        document.querySelectorAll(".sample").forEach((item) => item.classList.remove("is-active"));
        render();
      });
    });

    authTabs.addEventListener("click", (event) => {
      const button = event.target.closest(".auth-tab");
      if (!button) return;

      showAuthPanel(button.dataset.panel);
    });

    clientLoginForm.addEventListener("submit", async (event) => {
      event.preventDefault();

      if (!hasClientPassword()) {
        clientLoginMessage.textContent = "El administrador aun no ha creado la contrasena de cliente.";
        return;
      }

      if (await passwordHash(clientPassword.value) !== clientPasswordCode()) {
        clientLoginMessage.textContent = "Contrasena de cliente incorrecta.";
        return;
      }

      sessionStorage.setItem(SESSION_KEY, "client");
      clientPassword.value = "";
      clientLoginMessage.textContent = "";
      setAccess("client");
    });

    adminLoginForm.addEventListener("submit", async (event) => {
      event.preventDefault();

      const emailOk = adminEmail.value.trim().toLowerCase() === ADMIN_EMAIL;
      const passwordOk = await adminPasswordMatches(adminPassword.value);

      if (!emailOk || !passwordOk) {
        adminLoginMessage.textContent = "Correo o contrasena de administrador incorrectos.";
        return;
      }

      sessionStorage.setItem(SESSION_KEY, "admin");
      adminEmail.value = ADMIN_EMAIL;
      adminPassword.value = "";
      adminLoginMessage.textContent = "";
      setAccess("admin");
    });

    changeClientPasswordForm.addEventListener("submit", async (event) => {
      event.preventDefault();

      if (!await adminPasswordMatches(adminCurrentPassword.value)) {
        clientPasswordMessage.textContent = "La contrasena de administrador no coincide.";
        return;
      }

      if (newClientPassword.value.trim().length < 4) {
        clientPasswordMessage.textContent = "Usa una clave cliente de al menos 4 caracteres.";
        return;
      }

      localStorage.setItem(CLIENT_PASSWORD_KEY, await passwordHash(newClientPassword.value));
      adminCurrentPassword.value = "";
      newClientPassword.value = "";
      clientPasswordMessage.textContent = "Clave cliente cambiada.";
    });

    logoutButton.addEventListener("click", () => {
      sessionStorage.removeItem(SESSION_KEY);
      clientPasswordMessage.textContent = "";
      setAccess("");
    });

    window.addEventListener("resize", render);
    authTabs.style.display = "";
    showAuthPanel(location.hash === "#admin" ? "adminPanel" : "clientPanel");
    setAccess(sessionMode());
    render();
  </script>
</body>
</html>

