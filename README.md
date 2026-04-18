# bach-cello
An extension of Bach's cello suites using dissonance optimization for Independent Work for the Program in Applied and Computational Mathematics.

Bach's Cello Suites are written for solo instrument but are widely believed to imply hidden polyphony (countermelodies that exist in the harmonic structure but are never written on the page). This project asks whether an algorithm, guided by a dissonance model derived from acoustic physics, can reconstruct something musically coherent as that second voice.

# Components of the project

1. Acoustic dissonance model: derives chord roughness from first principles using the Plomp-Levelt psychoacoustic curve, grounded in the harmonic series rather than music theory rules
2. Markov chain validation:  fits an empirical transition model to Bach's 428 chorales and uses maximum likelihood estimation to tune the cost function against Bach's actual harmonic choices
3. Viterbi generation: uses dynamic programming to find the globally optimal hidden voice for a Cello Suite movement under the validated cost function

# File Tree
'''
.
bach-cello/
├── src/
│   ├── dissonance.py        # Plomp-Levelt roughness function and chord dissonance
│   ├── cost_function.py     # Transition cost combining motion, dissonance, and counterpoint violations
│   ├── markov.py            # Markov chain fitting, MLE lambda tuning, entropy rate
│   └── generator.py         # Viterbi algorithm and MusicXML export
├── scripts/
│   ├── run_dissonance_plots.py  # Generates interval dissonance verification plot
│   ├── run_validation.py        # Runs full chorale validation pipeline, saves figures and tuned lambdas
│   └── run_generator.py         # Runs Viterbi on Cello Suite No. 1 Prelude, exports score
├── figures/                 # Generated plots (gitignored)
├── data/                    # Exported data and tuned_lambdas.json
├── report/
│   └── main.tex             # LaTeX report
└── README.md
'''
# Dependencies

music21 — symbolic music parsing and Bach chorale corpus
numpy — linear algebra (stationary distribution, matrix operations)
scipy — MLE optimization (Nelder-Mead)
matplotlib — figures
