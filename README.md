# Induction and Alternating Current

This is an interactive, browser-based demo of electromagnetic induction, inductance, electromagnetic oscillations, and AC circuits. It comes as two separate pages, one in English and one in Korean.

Created by **Claude Opus 5.5**, based on the lecture notes by **Sang Hoon Lee (이상훈)**.

> **한국어 요약:** 패러데이 유도 법칙, 렌츠 법칙, 유도용량과 자체유도, RL 회로, 상호유도, LC·RLC 진동, 교류 RLC 회로와 공명, 교류의 일률, 변압기를 직접 조작해 볼 수 있는 인터랙티브 웹 데모입니다. 이상훈(Sang Hoon Lee)의 강의 노트를 바탕으로 Claude Opus 5.5가 만들었습니다. 한국어 페이지는 `induction-ko.html`입니다.

## Files

| File | Description |
| --- | --- |
| `induction-en.html` | American English version |
| `induction-ko.html` | Korean version (한국어) |
| `README.md` | This file |

Each page is a single self-contained HTML file with inline CSS and JavaScript. There is no build step and there are no dependencies. The only external request is to Google Fonts for IBM Plex Sans KR. If that request fails, the page falls back to system fonts. Each page links to the other language from its top bar.

## Running it

Open either file directly in a modern browser, or serve the folder locally:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000/induction-en.html
```

### Publishing on GitHub Pages

1. Push these files to a repository.
2. In **Settings → Pages**, choose **Deploy from a branch**, then select your branch and the root folder.
3. Visit `https://<user>.github.io/<repo>/induction-en.html` or `.../induction-ko.html`.

These pages can share a repository with the companion demos on DC circuits (`circuits-*.html`), RC circuits (`rc-*.html`), and magnetism (`magnetism-*.html`). The file names don't collide.

## What's inside

The ten sections follow the order of the lecture notes. Every value is recomputed live as you move the controls.

1. **Faraday's law:** A bar magnet moves toward and away from a coil wired to a galvanometer. You can move it by hand or let it swing back and forth on its own. The page plots the flux Φ<sub>B</sub> and the induced emf ℰ = −N dΦ<sub>B</sub>/dt live. It also shows the induced field and current, and whether the coil pushes the magnet away or pulls it back.
2. **Lenz's law:** There are four cases, with **B** pointing up or down and growing or shrinking. For each one the page shows the induced field **B**<sub>ind</sub> and the direction of the current.
3. **Induction and energy:** A loop is pulled out of a field region at constant speed. The page gives ε = BLv, i = BLv/R, and the opposing force B²L²v/R. Two bars show that the rate of work done by the pull equals the rate of heating, i²R. A note covers eddy currents.
4. **Inductance and self-induction:** A solenoid's inductance is computed from L = μ₀n²lA. You drag the current yourself, or use the ramp buttons, and watch ε<sub>L</sub> = −L di/dt oppose the change.
5. **RL circuit:** This is a live circuit with a two-way switch, where i(t) and V<sub>L</sub>(t) are traced over theory curves. A loop-rule bar shows ℰ = iR + V<sub>L</sub>. Power bars show that ℰi equals dU<sub>B</sub>/dt plus i²R, and the stored energy U<sub>B</sub> = ½Li² is displayed.
6. **Mutual induction:** The current in coil 1 either switches on, holds, and switches off, or follows a sine wave. The emf in coil 2, ε₂ = −M di₁/dt, appears in a graph and on a galvanometer.
7. **LC and RLC oscillations:** A charged capacitor is released into an inductor. The charge on the plates, the field around the coil, and energy bars for U<sub>E</sub>, U<sub>B</sub>, and heat are animated together. Graphs show q(t) with the damping envelope and the energies sloshing back and forth. The motion is computed by numerical integration (RK4) and shown 50× slower than real time.
8. **Driven RLC circuit:** A rotating phasor diagram shows ℰ<sub>m</sub>, V<sub>R</sub>, V<sub>L</sub>, V<sub>C</sub>, and I, along with their projections onto the vertical axis. The page also draws the emf and current waveforms and a resonance curve of I against f<sub>d</sub>. It reports X<sub>L</sub>, X<sub>C</sub>, Z, I, and φ, labels the circuit as inductive, capacitive, or at resonance, and has a "Tune to resonance" button.
9. **AC power:** For the same circuit, the page plots the instantaneous i²R, the source power ℰi, and their average. It gives rms values and the power factor, and calculates P<sub>avg</sub> two ways to show they agree. A note explains that household 220 V rms has a peak of 311 V.
10. **Transformer:** An ideal transformer with adjustable N<sub>p</sub>, N<sub>s</sub>, V<sub>p</sub>, and load R. The page gives V<sub>s</sub>, I<sub>s</sub>, I<sub>p</sub>, R<sub>eq</sub> = (N<sub>p</sub>/N<sub>s</sub>)²R, and power in = power out. A transmission example shows how raising the line voltage cuts the I²R loss.

## Notes on the model

- **Faraday section:** The magnet's field on the axis is modeled with a simple dipole-like falloff. The numbers are illustrative.
- **Real time:** The RL circuit and the mutual-induction section run in real time.
- **LC oscillations:** The LC section runs 50× slower than real time, and its readouts are the real values.
- **Phasor speed:** The phasor diagram rotates at a fixed, slow display speed whatever driving frequency is chosen.
- **Line loss example:** The transmission example uses 1 MW sent through lines with 5 Ω of total resistance. These values are illustrative.
- **Motion and theme:** The pages follow the system's light or dark setting. The RL simulation starts paused under `prefers-reduced-motion`, and the decorative header animation stays still.

## Credits

- Lecture notes: Sang Hoon Lee (이상훈)
- Demo design and code: Claude Opus 5.5

## License

No license has been chosen yet. Before publishing, add a `LICENSE` file if you want others to be able to reuse the code. Also confirm with the author of the lecture notes how their material may be shared.
