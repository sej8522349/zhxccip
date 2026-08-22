---
title: "Peptide Molecular Weight Formula — Superpower"
date: 2029-07-03 14:11
author: Grace Nakamura
---

# Peptide Molecular Weight Formula — Superpower

[Molecular Weight Formula](https://reboundworks.escortskhi.com/)

The Formula

Peptide molecular weight is calculated from the amino acid sequence using residue masses — the mass of each amino acid after subtracting the water molecule lost during peptide bond formation.

MW (Da) = Sum of all residue masses + 18.010565 Da (water, to account for the free N- and C-termini)

Residue mass = Amino acid molecular weight − 18.010565 Da

For modifications: add the modification mass algebraically (positive for additions, negative for losses)

When amino acids link via peptide bonds, a water molecule is released at each junction. A peptide with N residues has formed (N − 1) peptide bonds, losing (N − 1) water molecules during synthesis. The residue mass table accounts for this: it lists the mass of each amino acid already reduced by one water molecule. Summing the residue masses for a complete sequence, then adding back one water molecule to represent the intact free N- and C-termini, gives the final peptide MW. Kozlowski, in a 2021 paper in Nucleic Acids Research, documented how IPC 2.0 uses residue-level charge contributions for isoelectric point prediction, with an underlying residue-mass framework — a reference implementation of the arithmetic described here. A validated residue mass reference for manual calculation is maintained at the ExPASy ProtParam tool (Swiss Institute of Bioinformatics).

How to Calculate It Yourself

The steps below walk through the sequence-to-MW arithmetic manually.

Write down the one-letter or three-letter amino acid sequence of your peptide. Confirm the sequence from a primary reference or synthesis certificate — transcription errors in the sequence propagate directly to the MW calculation.

Choose your mass type: monoisotopic or average. For high-resolution mass spectrometry applications (Orbitrap, Q-TOF instruments), use monoisotopic masses. For lower-resolution applications or larger peptides, average masses are appropriate. Use one type consistently throughout the calculation.

Look up the residue mass for each amino acid. Use a validated table (ExPASy or equivalent). Common residue masses (monoisotopic): G = 57.02146, A = 71.03711, V = 99.06841, L/I = 113.08406, P = 97.05276, F = 147.06841, W = 186.07931, M = 131.04049, S = 87.03203, T = 101.04768, C = 103.00919, Y = 163.06333, H = 137.05891, D = 115.02694, E = 129.04259, N = 114.04293, Q = 128.05858, K = 128.09496, R = 156.10111, water = 18.01056.

Sum all residue masses for your complete sequence. Each residue contributes once. For a 15-residue peptide, sum 15 values.

Add 18.010565 Da (monoisotopic water) or 18.0153 Da (average water) to account for the free termini. This step restores the water molecule that represents the intact N-terminus (H−) and C-terminus (−OH).

Account for modifications, if any. Add the mass of any N-terminal modifications (acetylation: +42.011 Da; formylation: +27.995 Da). Add the mass of any C-terminal modifications (amidation: −0.984 Da). Add modification masses for PEGylation, DAC, phosphorylation (+79.966 Da per site), or disulfide bonds (−2.016 Da per bridge).

The result is the monoisotopic or average MW of your peptide, in Daltons. Verify by comparing against a reference value from the literature or a validated tool such as ExPASy ProtParam or PubChem for characterized compounds.

The Math in Detail

Breaking the calculation into distinct steps surfaces each assumption and makes errors easier to identify.

Monoisotopic vs. average mass

Monoisotopic mass is the sum of the most abundant stable isotopes of each element: ¹H = 1.0078250 Da, ¹²C = 12.0000000 Da, ¹⁴N = 14.0030740 Da, ¹⁶O = 15.9949146 Da, ³²S = 31.9720707 Da. Average (chemical) mass uses the weighted average across all naturally occurring stable isotopes, accounting for their natural abundance. For hydrogen, average mass = 1.00794 Da vs. monoisotopic 1.00782 Da — a small difference per atom that accumulates across a peptide's hundreds of atoms.

Frese and colleagues, in a 2011 paper in the Journal of Proteome Research, documented that high-resolution mass spectrometry instruments require monoisotopic mass for accurate peptide identification. Shen and colleagues confirmed in a 2012 paper that CID, HCD, and ETD fragmentation methods all require defined mass accuracy derived from the appropriate mass table. For peptides below approximately 1,500 Da, the monoisotopic peak is the dominant peak in the isotope envelope; for larger peptides, higher isotope peaks become more abundant, and the distinction between monoisotopic and average mass becomes practically important for instrument-database matching.

Residue masses and water

The fundamental arithmetic: an amino acid has a molecular formula and a molecular weight. A residue is what remains after one water molecule is removed during peptide bond formation. For glycine (G): full MW = 75.032 Da, residue mass = 57.021 Da (after −18.011 Da for water). Summing residue masses across the full sequence accounts for all internal peptide bonds. The final +18.011 Da step restores the single water molecule representing the intact free termini (one H on the N-terminus, one OH on the C-terminus). Kozlowski, in the 2016 IPC paper in Biology Direct, documented how the pI calculation algorithm defines residue-level charge and mass contributions using the same residue mass framework described here.

Unit conversion reference

1 Da (Dalton) = 1 g/mol — Daltons and g/mol are numerically equivalent for molecular mass expressions.

1 kDa = 1,000 Da — Larger peptides and proteins are expressed in kDa for readability.

Monoisotopic water = 18.010565 Da — Added at the end of every sequence MW calculation.

Average water = 18.0153 Da — Use when working with average mass tables throughout.

Renal clearance threshold: Peptides below approximately 60 kDa pass through the glomerular filtration membrane; most therapeutic peptides (1–10 kDa) are cleared renally.

Thanks for signing up!

Check your inbox — your first issue is on the way. We send clinically reviewed health science, never spam.

Worked Example

The following examples use two well-characterized therapeutic peptides with published MW values in the primary literature. They illustrate the calculation at two different scales.

Example 1: PTH(1-34) / teriparatide (34 residues, MW 4,117 Da)

PTH(1-34) (teriparatide) is a 34-residue FDA-approved therapeutic peptide with a well-documented MW of approximately 4,118 Da (average mass). Merutka and colleagues referenced this MW in their 2016 reconstitution stability study, using teriparatide as a model peptide to examine how reconstituted PTH(1-34) concentration and temperature affect stability. The calculation follows the same residue-sum procedure: sum 34 residue masses, add 18.011 Da water. At 34 residues, the monoisotopic mass and average mass begin to diverge more noticeably — the average mass (approximately 4,118 Da) and monoisotopic mass (approximately 4,115.2 Da) differ by about 2 Da, which is detectable in high-resolution MS.

The second worked example illustrates the same arithmetic on a smaller, non-approved research peptide — BPC-157 is used here strictly as a well-characterized analytical reference compound.

Example 2: BPC-157 (15 residues, MW 1,419 Da)

BPC-157 is used here as a technical example of a well-characterized 15-residue peptide. BPC-157 is not FDA-approved for any indication and is not on FDA's list of bulk drug substances eligible for 503A compounding; it is not lawfully available through US compounding pharmacies as of April 2026.

Sequence: Gly-Glu-Pro-Pro-Pro-Gly-Lys-Pro-Ala-Asp-Asp-Ala-Gly-Leu-Val (GEPPPGKPADDAGLV)

Sikiric and colleagues explicitly reported BPC-157's MW as 1,419 Da in their IBD trial documentation in Inflammopharmacology in 2006. Seiwerth and colleagues confirmed the 15-residue pentadecapeptide structure in a 2021 review in Frontiers in Pharmacology.

Manual residue sum (monoisotopic): G (57.021) + E (129.043) + P (97.053) + P (97.053) + P (97.053) + G (57.021) + K (128.095) + P (97.053) + A (71.037) + D (115.027) + D (115.027) + A (71.037) + G (57.021) + L (113.084) + V (99.068) = 1,400.734 Da.

Add water: 1,400.734 + 18.011 = 1,418.745 Da monoisotopic mass.

The literature value of 1,419 Da is the rounded average mass — consistent with the monoisotopic calculation above. This agreement confirms the formula and the sequence. Qian Cutrone and colleagues documented in 2017 that MW verification by mass spectrometry is standard quality-control practice in pharmaceutical peptide characterization.

Common residue masses for reference

Glycine (G): 57.02146 Da monoisotopic / 57.0519 Da average

Alanine (A): 71.03711 / 71.0788

Valine (V): 99.06841 / 99.1326

Leucine / Isoleucine (L/I): 113.08406 / 113.1594

Proline (P): 97.05276 / 97.1167

Phenylalanine (F): 147.06841 / 147.1766

Tryptophan (W): 186.07931 / 186.2132

Methionine (M): 131.04049 / 131.1926

Serine (S): 87.03203 / 87.0782

Threonine (T): 101.04768 / 101.1051

Cysteine (C): 103.00919 / 103.1388

Tyrosine (Y): 163.06333 / 163.1760

Histidine (H): 137.05891 / 137.1411

Aspartate (D): 115.02694 / 115.0886

Glutamate (E): 129.04259 / 129.1155

[Molecular Weight Formula Superpower](https://neurocurrent.china-akan.com/)

Asparagine (N): 114.04293 / 114.1038

Glutamine (Q): 128.05858 / 128.1307

[Peptide Molecular](https://reboundworks.escortskhi.com/blog/2077976705.html)

Lysine (K): 128.09496 / 128.1741

Arginine (R): 156.10111 / 156.1875

[Peptide Molecular Weight](https://metabolic-horizon.bbsxyxy.com/blog/1211208941.html)

Water (terminus addition): 18.010565 monoisotopic / 18.0153 average

Molecular Weight and Peptide Modifications

The sequence-based calculation gives the MW of the unmodified linear peptide. Post-translational or synthetic modifications alter the calculated value.

Common modifications and their mass effects

N-terminal acetylation: +42.011 Da. Adds an acetyl group (CH₃CO) in place of the free amine hydrogen.

C-terminal amidation: −0.984 Da. Replaces the C-terminal hydroxyl (OH) with an amino group (NH₂), a common modification in therapeutic peptides to resist C-terminal peptidase degradation.

[Formula Superpower](https://innate-signal.jcesqc8.com/)

Disulfide bond formation: −2.016 Da per bridge. Two cysteine residues lose one hydrogen each when their thiol groups form a covalent S–S bond.

Phosphorylation (serine, threonine, or tyrosine): +79.966 Da per site.

DAC modification (CJC-1295): +approximately 300 Da for the drug affinity complex moiety attached to lysine side chains. CJC-1295's total MW is approximately 3,647 Da (average mass, computed from the published sequence with the DAC modification), versus approximately 3,357 Da for unmodified GHRH(1-29) — a difference of about 290 Da attributable to the DAC modification. CJC-1295 is not FDA-approved for any indication; FDA's Pharmacy Compounding Advisory Committee has recommended against adding CJC-1295 to the 503A bulks list, and it is not lawfully available through US compounding pharmacies as of April 2026 — the MW discussion here is provided for analytical reference only. Teichman and colleagues (JCEM 2006) reported the clinical pharmacokinetics of CJC-1295, and Jetté and colleagues (Endocrinology 2005) characterized hGRF(1-29)-albumin bioconjugates that established the DAC-extension mechanism.

PEGylation: Adds the mass of the entire PEG polymer chain, which can range from several hundred to several thousand Da depending on PEG MW. This dramatically increases total MW and alters renal clearance.

Limits of This Math

The sequence-based MW calculation is highly accurate for unmodified linear peptides with a known sequence. Several factors limit or complicate the result.

Monoisotopic vs. average mass — choosing the right type

For peptides above approximately 2,000 Da, the monoisotopic peak is no longer the most abundant peak in the mass spectrum — higher-mass isotope peaks become dominant. In those cases, high-resolution instruments report a measured mass closer to the average mass, not the monoisotopic. Search algorithms including SEQUEST, MASCOT, and OMSSA rely on calculated peptide masses for precursor matching, as Good and colleagues discussed in a 2010 ETD-algorithm analysis in Proteomics — and that mass type consistency between the database and the instrument is required for correct identification. Using monoisotopic masses for a large peptide measured on an instrument reporting near-average mass will produce a systematic mismatch.

Sequence uncertainty and modified residues

The calculation is only as accurate as the sequence input. Leucine and isoleucine have identical residue masses (113.08406 Da) and cannot be distinguished by mass alone — they require ETD or ECD fragmentation for sequence-level identification. Vizioli and Carducci (1999) described capillary electrophoresis methods for monitoring synthetic peptide purity — techniques that depend on an accurate reference sequence and expected MW. Any error in the sequence propagates directly to the MW result.

Unaccounted modifications in research-grade peptides

Research-grade peptide products may contain modifications not present in the literature sequence — truncations, oxidized methionines, or synthesis byproducts. The calculated sequence MW assumes a pure, correctly synthesized peptide. Wang and colleagues' 2014 JUMP database search tool (Molecular & Cellular Proteomics) is one example of a tag-based identification method that uses precursor mass matching before sequence scoring — meaning unexpected modifications that shift the observed mass will cause the peptide to fail database matching, which can be useful as a quality-control indicator.

When to use experimental verification

Calculated MW is a prediction. For pharmaceutical quality control and research applications requiring high confidence in compound identity, experimental mass spectrometry verification is standard. Dawson and colleagues, in a 2000 paper in the Journal of Peptide Science, documented that MW from sequence calculation is followed by MS confirmation as a standard characterization workflow for synthetic peptides. Bern and colleagues, in a 2006 paper in the Journal of Computational Biology, established the mass-graph approach to de novo sequencing, confirming that fragment mass differences between adjacent ions equal amino acid residue masses — which is how experimental MW is reconstructed from MS data without a prior sequence assumption.

What to Know Before Starting a Peptide Protocol

Molecular weight calculation is primarily a research and analytical tool. For those approaching peptide science from a clinical context — evaluating candidacy for provider-supervised peptide therapy rather than characterizing a synthesis product — the relevant starting point is baseline biomarker data rather than sequence arithmetic.

Providers evaluating candidacy for FDA-approved peptide medications — including semaglutide, tirzepatide, teriparatide, and tesamorelin — typically review baseline markers that reflect the biological systems the compound will affect: IGF-1 levels for GH-axis compounds, metabolic markers including fasting glucose and HbA1c for metabolic compounds, and kidney function (eGFR) for any injectable compound subject to renal clearance. The research peptides referenced earlier in this article (BPC-157, CJC-1295) are used as analytical examples only; they are not FDA-approved and are not lawfully available through US compounding pharmacies as of April 2026. Nugrahadi and colleagues documented that peptide MW directly influences renal clearance threshold — which is why kidney function context is part of baseline evaluation for injectable compounds in the therapeutic MW range. Setting up baseline biomarker testing before any clinical intervention establishes the objective reference that makes subsequent monitoring interpretable.

That principle — data before decisions — is foundational to Superpower's approach to preventive health: objective biomarker measurement first, clinical decisions second, with a licensed provider at every step.

This page is provided for educational, research, and laboratory reference purposes only. The formulas and conversion references on this page do not constitute medical advice, a prescription, or a dosing recommendation. Peptide administration should be supervised by a licensed healthcare provider. Superpower Health does not prescribe, compound, or facilitate access to research peptides that are not FDA-approved. Superpower Health connects members with licensed providers who may prescribe compounded semaglutide or tirzepatide (not FDA-approved; prepared by 503A pharmacies) or FDA-approved versions where clinically appropriate; details are on each compound's dedicated page.

Frequently Asked Questions

[Molecular Weight Formula](https://taihpeptide.com/)

What is peptide molecular weight?

Peptide molecular weight (also called peptide mass) is the total mass of a peptide molecule, calculated as the sum of the masses of its constituent amino acid residues plus the mass of a water molecule added back to account for the free N- and C-termini. During peptide bond formation, one water molecule is lost per bond — so a peptide with N amino acids has (N − 1) water molecules removed during synthesis. The final molecular weight calculation adds one water molecule back to account for the intact termini. The result is typically expressed in Daltons (Da) or, equivalently, grams per mole (g/mol).

What is the difference between monoisotopic mass and average mass?

Monoisotopic mass uses the exact atomic mass of the most abundant stable isotope of each element (¹H = 1.00782 Da, ¹²C = 12.00000 Da, ¹⁴N = 14.00307 Da, ¹⁶O = 15.99491 Da, ³²S = 31.97207 Da). Average mass uses the naturally weighted average across all naturally occurring isotopes of each element, accounting for their natural abundance ratios. For small peptides, the difference is small. For peptides above approximately 1,500 Da, the values diverge meaningfully. Frese and colleagues, in a 2011 analysis in the Journal of Proteome Research, documented that mass accuracy requirements for peptide identification in high-resolution MS depend on which mass type is used. Monoisotopic mass is the standard for high-resolution mass spectrometry identification; average mass is used in lower-resolution contexts and for larger molecules where the monoisotopic peak is not the most abundant.

How do I calculate peptide molecular weight from a sequence?

Sum the residue masses of all amino acids in the sequence (using either monoisotopic or average mass tables, consistently), then add 18.010565 Da (monoisotopic water) or 18.0153 Da (average water) to account for the free N- and C-termini. Residue mass is the mass of each amino acid minus water (reflecting the water lost when that residue forms peptide bonds). Tools including ExPASy ProtParam and the IPC 2.0 calculator perform this arithmetic for arbitrary sequences. Kozlowski, in a 2021 paper in Nucleic Acids Research, documented that IPC 2.0 uses residue-level charge contributions for isoelectric point prediction, with an underlying residue-mass framework.

Why does molecular weight matter for peptide dosing?

Molecular weight determines the molar-to-mass conversion ratio, which is required any time a dose is expressed in molar units (nmol, pmol) rather than mass units (mg, mcg). For the same mass dose, a heavier peptide contains fewer moles than a lighter one — which can be relevant when comparing receptor occupancy between compounds of different sizes. Somatropin (recombinant hGH) has a molecular weight of approximately 22,124 Da; Liedert and colleagues (BMC Clinical Pharmacology 2010) reported PK comparisons across somatropin formulations that rely on this MW for molar dose calculations. For most clinical reconstitution calculations, mass units (mg, mcg) are used throughout and MW is not required — but in research contexts involving receptor binding or pharmacokinetic modeling, MW is the foundational parameter.

What is the molecular weight of BPC-157?

BPC-157 is a research peptide without FDA approval; it is not on FDA's list of bulk drug substances eligible for 503A compounding and is not lawfully available through US compounding pharmacies as of April 2026. The molecular weight calculation below is provided for analytical reference, not as dosing or access guidance. BPC-157 (sequence GEPPPGKPADDAGLV) has a molecular weight of 1,419 Da. This value is explicitly documented in multiple peer-reviewed publications. Sikiric and colleagues reported BPC-157's MW as 1,419 Da in their IBD trial documentation published in Inflammopharmacology in 2006. Seiwerth and colleagues confirmed the pentadecapeptide structure (15 amino acids) in a 2021 review in Frontiers in Pharmacology, and the MW can be independently verified by summing the monoisotopic residue masses of the GEPPPGKPADDAGLV sequence and adding water.

Does molecular weight change with peptide modifications?

Yes. Any chemical modification adds or removes mass from the calculated sequence MW. PEGylation adds the mass of the PEG chain. DAC modification (used in CJC-1295) adds approximately 300 Da of drug affinity complex. (CJC-1295 is not FDA-approved; FDA's Pharmacy Compounding Advisory Committee has recommended against adding CJC-1295 to the 503A bulks list, and it is not lawfully available through US compounding pharmacies.) Acetylation of the N-terminus adds 42.011 Da. Amidation of the C-terminus removes 0.984 Da (replacing OH with NH₂). Disulfide bond formation removes 2.016 Da (two hydrogens lost). Teichman and colleagues reported CJC-1295's MW as approximately 3,647 Da including its DAC modification — confirming that modifications increase MW beyond the raw sequence prediction. Any calculator that uses only the amino acid sequence will undercount MW for modified peptides.

How is molecular weight used in mass spectrometry?

In mass spectrometry, the measured mass-to-charge ratio (m/z) of a peptide ion is matched against a calculated MW to confirm identity. Database search tools including MASCOT, SEQUEST, and OMSSA calculate MW for all candidate sequences in the database and match them to the observed precursor mass within a defined tolerance window. The original MASCOT algorithm paper by Perkins and colleagues in Electrophoresis in 1999 documented that MASCOT uses calculated peptide MW for precursor mass matching in database-driven proteomics identification. Accuracy at the sub-Dalton level is required for confident identification — which is why the monoisotopic vs. average mass distinction matters in high-resolution instrument contexts.

What is the clinical relevance of knowing a therapeutic peptide's molecular weight?

For clinical and formulation applications, MW influences renal clearance threshold (peptides below approximately 60 kDa pass through the glomerular filtration membrane), oral bioavailability (smaller peptides have higher passive permeability through intestinal epithelium), and half-life estimation in pharmacokinetic modeling. Nugrahadi and colleagues, in a 2023 review in Pharmaceutics, documented that MW influences absorption kinetics, renal clearance threshold, and half-life across therapeutic peptide classes. Semaglutide's molecular weight (approximately 4,114 Da) is embedded in its pharmacokinetic characterization; Yang and colleagues published a 2024 systematic review of semaglutide clinical PK in Drug Design, Development and Therapy.

## More Resources

- [Stop: Why You Need a Doctor’s Note for Driving Safety Now | Ubie Doctor's Note](https://github.com/d3urfp7gsz/viwpxrf/blob/main/misc/2029-06-09-stop-why-you-need-a-doctor-s-note-for-driving-safety-now-ubie-doctor-s.md)
- [What is a Skinny Shot? San Diego Skin Shot for Weight Loss Guide by LIVVNatural.com](https://github.com/dxcyubq2h0/czeykaj/blob/main/qa/2029-06-04-what-is-a-skinny-shot-san-diego-skin-shot-for-weight-loss-guide-by-liv.md)
- [Mobile Iron IV Therapy Boston](https://github.com/vm0zes5twa/gvbgltz/blob/main/misc/2029-06-10-mobile-iron-iv-therapy-boston.md)
- [Sudden Confusion? Why Your Cerebrum Is Misfiring—Act Now | Ubie Doctor's Note](https://github.com/nhd4l1jjtt/ohgmyy/blob/main/qa/2029-04-26-sudden-confusion-why-your-cerebrum-is-misfiring-act-now-ubie-doctor-s.md)
- [Stop! Why Your Liver, Not a Colonic, Is the Real Detox Science | Ubie Doctor's Note](https://github.com/pfjzag6ves/hwbjnj/blob/main/guide/2029-04-21-stop-why-your-liver-not-a-colonic-is-the-real-detox-science-ubie-docto.md)
