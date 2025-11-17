## Tools
- ChatGPT

## Where AI was used
All changes were reviewed, edited, and tested by us before committing.

- `operations/bitvec.py` — ripple-carry adder helpers, two’s-complement negate
- `operations/twos_complement.py` — 32-bit encode/decode, sign/zero-extend (forbidden-ops compliant)
- `operations/alu.py` — ADD/SUB via bit-adder chain; N/Z/C/V flag rules
- `operations/shifter.py` — SLL/SRL/SRA implemented without host shifts
- `operations/mdu.py` — shift-add multiplier and restoring divider
- `operations/fpu_f32.py` — pack/unpack, mul, add, sub
- `operations/fcsr.py` — frm + sticky `fflags` with small helpers.
- `tests`

## Example prompts
- "Explain two’s-complement for 32-bit integers. Show how to encode/decode positive and negative values."
- "Why does fmul_f32 return 0x7F800000 for 1.5×1.5? Show normalize/round steps and patch."
- "Our shifter test expects ungroupped binary but bits_to_str groups by nibble, can you adjust the test?"
- "Create fcsr.py with frm and sticky fflags and minimal tests."
- "I get ImportError: attempted relative import; restructure tests/imports to match package layout."
- "Can you help me implement encode_twos_complement(value:int)->{bin,hex,overflow_flag} and decode_twos_complement(bits)->{value} for width=32. Don’t use Python’s + - * / % << >> in the implementation"
- "Can you help me implement a ripple-carry adder add_rca(a_bits, b_bits, cin) using only boolean ops on single bits"
- "Provide pytest cases for: 0x7FFFFFFF + 1, 0x80000000 - 1, -1 + -1, and 13 + (-13)"
- "Can you help me implement shift-add multiplication for 32×32 to 64 with a per-iteration trace (accumulator, multiplier, step). Return low word (MUL) and optionally high word (MULH/MULHU/MULHSU)."
- "What’s the sign rule for MULHSU vs MULH vs MULHU?"
- "Explain IEEE-754 float32 fields (sign, exponent with bias, fraction). Show how to pack/unpack a Python decimal value without using Python float ops in the implementation."
- "How would I go about implementing fadd_f32 and fsub_f32 with alignment (shift the smaller significand), add/sub, normalization, and ties-to-even."


```json
{"total_lines":2249, "ai_tagged_lines":900, "percent":40.0, "tools":["ChatGPT"], "method":"self estimate (We forgot track perline markers)"}
