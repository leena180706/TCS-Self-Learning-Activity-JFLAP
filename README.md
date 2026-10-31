
# JFLAP – Theory of Computation Lab

This repository contains my practical work and learning in Theory of Computation using JFLAP. It includes different finite automata and computational models with their purpose and working.

## Practical Work

### 1. Deterministic Finite Automaton (DFA)

**Experiment:** Checking strings with an even count of `a` and an odd count of `b`.

**JFLAP File:** `69_DFA_Even_a_Odd_b.jff`

The DFA checks the number of occurrences of `a` and `b` in an input string. It accepts a string only when the count of `a` is even and the count of `b` is odd.

**State details:**
- `q0` – Both `a` and `b` have even counts (Start state).
- `q1` – Odd count of `a` and even count of `b`.
- `q2` – Even count of `a` and odd count of `b` (Final state).
- `q3` – Both `a` and `b` have odd counts.

**Sample testing:**
- Accepted: `b`, `aab`, `abb`
- Rejected: `a`, `ab`, `bb`

### 2. Nondeterministic Finite Automaton (NFA)

**Experiment:** Recognizing binary-style strings over `{a, b}` that finish with `aa`.

**JFLAP File:** `69_NFA_Ending_With_aa.jff`

This NFA identifies whether the last two characters of an input string are `aa`. It uses multiple possible transitions to guess where the ending pattern begins.

**State details:**
- `q0` – Starting state; reads any number of `a`s and `b`s.
- `q1` – Detects a possible starting position of the final `aa`.
- `q2` – Reached after reading the second `a`; accepting state.

**Sample testing:**
- Accepted: `aa`, `aaa`, `baa`, `abaa`
- Rejected: `ab`, `aba`, `bb`

### 3. Conversion of NFA into DFA

**Experiment:** Converting a nondeterministic automaton into a deterministic automaton.

**JFLAP File:** `69_NFA_to_DFA_Conversion.jff`

In this practical, the NFA for strings ending in `aa` is converted into an equivalent DFA using the subset construction technique.

**Reachable DFA states:**
- `{q0}` – Initial state.
- `{q0, q1}` – Possible states after reading `a`.
- `{q0, q1, q2}` – Accepting state because it includes `q2`.

The subset method combines multiple NFA states into one DFA state. Any resulting subset containing the original final state `q2` is also a final state.

**Sample testing:**
- Accepted: `aa`, `aaa`, `baa`
- Rejected: `ab`, `aba`, `bb`

### 4. Moore Machine

**Experiment:** Replacing the pattern `100` with `101`.

**JFLAP File:** `69_Moore_Machine_100_to_101.jff`

This practical demonstrates a Moore machine designed to identify the sequence `100` and produce the modified sequence `101`.

**State details:**
- `q0` – Starting state.
- `q1` – Tracks the occurrence of `1`.
- `q2` – Tracks the sequence `10`.
- `q3` – Represents detection of the complete sequence `100`.

A Moore machine generates its output according to the state it reaches. The output assigned to each state determines the transformed sequence.

### 5. Mealy Machine

**Experiment:** Detecting whether a binary string ends in `01`.

**JFLAP File:** `69_Mealy_Machine_Ending_With_01.jff`

This Mealy machine checks the input sequence and identifies the pattern `01` at the end of a binary string. It produces output `1` when the pattern is detected and `0` for other transitions.

**State details:**
- `q0` – Initial state; no relevant `0` has been detected.
- `q1` – The most recently read symbol is `0`.
- `q2` – The pattern `01` has been detected.

**Sample testing:**
- Final output `1`: `01`, `101`, `1101`, `0101`
- Final output `0`: `100`, `111`, `1010`

---

**Tools Used:** JFLAP  
**Subject:** Theory of Computation
