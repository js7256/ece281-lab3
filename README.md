# Lab 3: Thunderbird Turn Signal

VHDL for ECE 281 [Lab 3](https://usafa-ece.github.io/ece281-book/lab/lab3.html)

Targeted toward Digilent Basys3. Make sure to install the [board files](https://github.com/Xilinx/XilinxBoardStore/tree/2018.2/boards/Digilent/basys3).

Tested on Windows 11.

![Waveform from thunderbird_fsm_tb](lab3waveform.png)

## Documentation:
I shot Maj Seery some questions over Teams. These questions were regarding my waveform. First, I was confused on why none of the right signals were present, so I showed Maj Seery and he said that I had the wrong testbench file pulled up on the waveform. Once I got the right signals, I noticed one of them had red X's, which according to Maj Seery, meant "high impedance." With this knowledge, I was able to fix my waveform to where no red things were present. Then, concerning finding the right value for k_div, I asked ChatGPT to find that for me. I also asked ChatGPT why my i_reset function doesn't work. It gave me some things to check for, which I feel like I checked already, so there was no help there. I also glanced ahead at some instructions that involved grounding unused LEDs. I asked ChatGPT how one does that in VHDL, and again, it wasn't helpful. However, I looked at the code that was already provided and turns out, that code was provided already, so it didn't matter. Other than that, I used my previous ICE 4 code as a sort of template/reference when I was stuck on how I implemented something. Other than that, no help was received. 

---

## Build the project

You can simply open `thunderbird.xpr` and Vivado will do the rest!

## GitHub Actions Testbench

The workflow uses the [setup-ghdl-ci](https://github.com/ghdl/setup-ghdl-ci) GitHub action
to run a *nightly* build of [GHDL](https://ghdl.github.io/ghdl/).

The workflow uses GHDL to analyze, elaborate, and run the entity specified in the `.github/workflows/testbench.yml`.

```yaml
env:
  TESTBENCH_ENTITY: myfile
```

If successful then GHDL will quietly exit with a `0` code.
If any of the `assert` statements fail **with** `severity error` then GHDL will cease the simulation and exit with non-zero code; this will also cause the workflow to fail.
