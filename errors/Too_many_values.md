problem: Error: Too many values for input signal account_rlp
when the  input account_rlp len in json == signal[len]

ERROR:
```
Error: Too many values for input signal account_rlp

signal account_rlp[164];
and the json input len == 164

pub fn format_inputs(&self) -> Result<String, Box<dyn std::error::Error>> {
    let inputs =json!({
        "state_root": self.state_root,
        "account_rlp": self.account_rlp,
        "account_rlp_len": self.account_rlp_len,
        "account_proof": self.account_proof,
        "account_proof_length":self.account_proof_length,
        "node_length":self.node_length,
        // "node_types" : self.node_types
    });
    Ok(inputs.to_string())
}

```
so the json input length and the circuit input len match but we still get the Too many values

resolve:
```
signal account_rlp[164] => signal input account_rlp[164];
//forgot the input word
```