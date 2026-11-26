Numerical verifications and computations for the paper
"The cycle line and the major arcs of the Syracuse characteristic function"
(A. Petojevic, S. Tamura)
Repository: https://github.com/apetoje/No14 (archive programs.zip)

Requirements: Python 3.13 with NumPy 2.5 and SciPy 1.18; GCC 13.3 (C17) for phi_tables.c.
The rigorous programs (marked [rigorous]) use only the Python decimal module and IEEE binary64 arithmetic
with explicit error bounds (Appendix A); no library transcendental function enters any inequality.
Numbering of theorems, tables and remarks refers to the current version of the paper.
Statements with analytic proofs are not listed; only computer-assisted results,
tables and numerical observations are.

Helper modules (imported by the other programs)
  syracuse_law.py        exact law of X_n mod 3^n
  psi_tables.py          exact tables phi_n(2^k) on all units for n <= 15
  rig.py                 [rigorous] decimal enclosures: pi (Machin), ln 2, x = log_2 3, exp, 2^z, cos/sin(2 pi z)
                         by Taylor series with explicit remainder; every value enlarged by 1e-40.
  selftest_decimal.py    Appendix A: independent check of the decimal exp and ln on 2500 random arguments
                         (largest relative difference 2.4e-57). Usage: python3 selftest_decimal.py

Section 3 (collisions)
  collisions_general.py  Remark after Corollary 3.4 ((3,4,{1}): bound 0.577 > M_1 = 0.5);
                         paragraph after Proposition 3.5 (Q_n for (3,4,{1,2}), n<=6, and (4,5,{1,2,3}), n<=5);
                         numerical paragraph after Conjecture 3.7 (R_n/gamma^n for (3,4,{1}), (4,5,{1});
                         R_n for (3,5,{1,2}), (4,5,{1,2}), (3,5,{1})).
                         Usage: python3 collisions_general.py 3 4 1 8   (p q digits nmax)
  resonance.py           Table 1 (correlations about the centres -1, 7, -5, 1 at n = 15);
                         T_n(h), |h| >= 2, stabilization, and T_17(1) = 0.73001 (beginning of Section 3.1).
  full_tables_energy.py  Q_n for n <= 17 (Table 2, Q_17 = 0.47182, Q_1 = 2/3, Q_2 = 10/21);
                         M_n for n <= 17; energy on the major arcs E_n and the ratios E_n/E_{n-1} (Section 12).
  collisions_23.py       Table 2 (Q_n and D_n(1), n <= 13).
  certificate_float.py   Theorem 3.15 / Remark 3.17: certificates at levels m = 1..4, Lambda_m and h(2,1).
                         Usage: python3 certificate_float.py m A iterations, e.g. 2 60 400 (saves cw_h_m2.npy).
  certificate_exact.py   Corollary 3.16: exact rational verification for m = 1, 2 (Lambda >= 0.877430, h(2,1) = 0.58988).
                         Usage: python3 certificate_float.py 2 60 400 ; python3 certificate_exact.py 2
  certificate_level5.py  [rigorous] Corollary 3.18 and Appendix A: certificate at level m = 5, Lambda >= 0.982944048,
                         min h = 0.0590, h(2,1) = 0.384323, hence M_n >= 0.2191 * 0.5724^{n-1}.
                         Usage: python3 certificate_level5.py 5 60 600 28   (saves cw_h_m5.npy; several minutes)
  correlation_minima.py  Remark 3.17: minima of U_n over all states, n <= 10.
  correlation_increments.py  Remark 3.17: max |U_n - U_{n-1}| far from the diagonal (about 0.23).
  cn_values.py           Paragraph after Proposition 3.22: 3^n c_n = 0.2857, 0.1449, ..., 0.0469 for n = 2, 4, ..., 14,
                         c_n = min over b not divisible by 3 of P(X_n = b mod 3^n). Usage: python3 cn_values.py 14

Section 5 (first exit, minor arcs)
  minor_arc_truncation.py  Remark 5.8: setting the minor arcs to zero above level 16 changes M_150 by 13.5 %.

Section 7 (real Syracuse variable)
  real_variable_tail.py  Remark 7.2: y P(Y > y) = 1.66, 1.87, 1.89 for y = 10, 100, 1000.

Section 8 (twisted major arcs)
  twisted_major_arcs.py  End of Section 8: largest values at +-(3^{n-1} - 2^k) for n = 12, 15 and the ratios
                         max outside M_n(R) / M_n for R = 0, 1, 2 and n = 6, 10, 15.
  check_exact_law.py     Agreement of the recursion tables with the exact law (Tao, Lemma 1.12) for n <= 6.

Section 9 (front equation and superposition)
  box_spectrum.py        Paragraph after Proposition 9.3: (1 - lambda(S)) S^2 for S = 20, ..., 90 and the
                         effective barrier s_b = -4.1.
  superposition_check.py Proposition 9.5 and Lemma 9.6: phi_n(2^j) = B_n(j) + sum_m phi_m(1) W^(m)_n(j), checked against
                         the exact tables for n = 8, 12, 15 (differences about 1e-17). Usage: python3 superposition_check.py
  check_identity.py      Proposition 9.5 in exit form (weights w_t), n = 6, 10, 13. Usage: python3 check_identity.py
  span_distance.py       Remark 9.7: distance of B_n from the span of the level fronts (one control per level).
                         Usage: python3 span_distance.py 20 30 40
  twisted_span.py        Remark 9.7: twisted families (conditioning on X_n mod 3^s) add no constraints.
                         Usage: python3 twisted_span.py check 10 2 ; python3 twisted_span.py span 2 20 30
  mirror_lift_check.py   Remark 9.7: lifts of 2^{-b} give central tails only at levels m with 3^{m-1} <~ 2n.
                         Usage: python3 mirror_lift_check.py

Section 10 (upper bound n^{-3/2} on the cycle line)
  killing_pq.py          Remark after Lemma 10.2: kernel masses 0.32 and 0.17 for (3,4) and (4,5).
  trivial_bound.py       Remark 10.7: supremum = rho, u* = 1 - x/2 = 0.2075, r(0.1) = 0.019, r(0.3) = 0.044.
  wave_harmonic.py       Remark 10.8 (variation of arg W on [-60,-5], about 0.34 pi) and Table 5, second row
                         (wave of Theorem 11.4, maximum at s* = -6.78).

Section 11 (archimedean part of the front)
  build_H4.py            Proposition 11.10: construction of H_1 (sup H_1 = 15.8944). Writes H4_params.json, H4_nodes.npy
                         (both included). Usage: python3 build_H4.py 18000 0.02 0.15 8
  build_H5.py            Proposition 11.10: construction of H_2 (source G + G_1, sup H_2 = 30.9366), hence
                         sup |V~(z) - (-z)_+| <= 30.94. Writes H5_params.json, H5_nodes.npy (both included).
                         Usage: python3 build_H5.py 18000 0.02 0.15 8
  verify_H1.py           [rigorous] Proposition 11.10 and Appendix A: H_1 >= G + K^T H_1 on all of R
                         (smallest lower bound 4.94e-5 on [-40,5], 1.23e-7 on [-80,-40]; y < -80 and y > 5 analytic).
                         Usage: python3 verify_H1.py   (about 10 s; creates gam_c_4096.npy, c = 3..8)
  verify_H2.py           [rigorous] Proposition 11.10: H_2 >= G + G_1 + K^T H_2 on all of R (same margins).
                         Usage: python3 verify_H2.py   (a few minutes)
  rigorous_front.py      [rigorous] Theorem 11.11(b) and Appendix A: front V^B_n for n <= N+1 = 20001 with error bound.
                         Writes front2_N20000.npz. Usage: python3 rigorous_front.py 20000   (long run)
  enclosure_PB.py        [rigorous] Theorem 11.11(b): S_N = -0.0163877 - 0.0811120 i (error <= 5.3e-9), tail bound
                         0.0150356 from Lemma 11.9(b) with H_1, hence |P^B| >= 0.06771.
                         Usage: python3 enclosure_PB.py 20000   (needs front2_N20000.npz, H4_params.json, H4_nodes.npy)
  explicit_constant.py   Theorem 11.11(c) and Appendix A: v = 3.9699, t_n = 7.97 sqrt((n-1) log n); the tail bound is
                         <= |P^B|/2 for all 226 <= n <= 20000 (0.03400 at n = 225, 0.03377 at n = 226) and a monotone
                         majorant is 4.5e-5 at n = 20000. Usage: python3 explicit_constant.py 20000
  conspiracy_cost.py     Remark 11.12: controls cancelling B_n on the line to relative accuracy 1e-3, with
                         max_m e^{0.6 m}|c'_m| = 0.22, 0.068, 0.036, 0.027 for n = 30, 40, 50, 60, compared with
                         max_m e^{0.549 m}|phi_m(1)| = 1.34 for the true central values.
                         Usage: python3 conspiracy_cost.py
  archimedean_part.py    Section 12, paragraph "The archimedean part": B_n of Lemma 9.6 for n <= 6000,
                         n^{3/2} e^{rho n} max|B_n| = 0.0241, ..., 0.0233 and the peak position 6.96, ..., 6.78;
                         the value e^{rho n} max|B_n| = 1.65e-5 at n = 150 (Section 12).
                         Usage: python3 archimedean_part.py 6000
  pairing_B.py           Section 12: floating-point approximations S_N of the conserved pairing P^B
                         (|S_N| = 0.1039, ..., 0.0860 for N = 200, ..., 3200). Usage: python3 pairing_B.py 3200
  window_major_arcs.py   The comparison value e^{rho n} M_n = 2.28e-3 at n = 150 (Section 12).

Section 12 (computation and conjectures)
  phi_tables.c           Theorem 12.1: full tables on all units for n <= 18 (M_n and the maxima).
                         Compile: gcc -O2 -o phi_tables phi_tables.c -lm ; run: ./phi_tables 18
  window_major_arcs.py   Theorem 12.1 and Table 3 (M_n and nx - k_n for n <= 150).
                         Usage: python3 window_major_arcs.py 150
  window_large_n.py      Table 4 (G_n, n G_n and nx - k_n up to n = 50000) and the interval [6.266, 7.292]
                         of the peak shift for 1000 <= n <= 50000 (long run).
  window_edge_check.py   Appendix A: independence of the values of the position of the left edge.
  window_profile.py      Table 5, first row (profile |G_20000(nx+s)|/max).
  window_reservoir_cut.py  Table 6 (n^{3/2} e^{rho n} M_n with and without the part s < -120 removed at n = 600).
  window_tilted_profile.py  Section 12: the distant reservoir of V_n near s = -230.
  general_pq_window.py   Table 7 and the peak shift interval [4.06, 5.07] for (3,4); agreement for left edges
                         -150, -300, -600 (Usage: python3 general_pq_window.py p q n0 NMAX J0 [v],
                         e.g. 3 4 10 12000 -150).
  full_tables_energy.py  Energy ratios E_n/E_{n-1} = 0.704, ..., 0.786 for n = 11, ..., 17.
  quartic_energy.py      Proposition 12.4: ratios F_n/F_{n-1} = 0.412, 0.452, 0.479, 0.533 for n = 6, 10, 12, 15
                         and the inequalities M_n^4 <= F_n <= Q_n M_n^2 for n <= 15. Usage: python3 quartic_energy.py
  conjecture_H_check.py  Table 8 (Conjecture 5.2 with sigma = (1/2) ln 3 up to m = 400) and the fitted rates
                         0.559 (maximum) and 0.561 (root mean square). Usage: python3 conjecture_H_check.py 400 -3000
  central_values.py      Caption of Table 8 (3^{m/2}|phi_m(1)| for m = 21, 51, 101, 151, 300) and the bound
                         |phi_m(1)| e^{sigma_c m} <= 2.4e-2 for 150 <= m <= 300. Usage: python3 central_values.py 300 -3000
