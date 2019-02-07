# Zero-knowledge proofs in identity systems
by Jordi Baylina &lt;<jordi@iden3.io>&gt; and David Suarez &lt;<david@iden3.io>&gt;


## Model of a ZKP

What's the model of a Zero-knowledge proof? 

<div style="text-align:center;"><img src="./media/ZKP.png" width=50% height=50%></div>

A ZKP can be described as a deterministic program (from now circuit) where there is a private input (secret) and a public output. Such a system is able to generate a proof of the private input which is a function of the private input itself and the circuit.

Which these variables a pairing function can be constructed such as depending on the circuit, the output and the proof (but still not the private input), a validation can be performed in terms of true or false, conforming the ZKP.


