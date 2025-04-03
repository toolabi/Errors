problem: empty zkey

circuits/mpt/mpt_0000.zkey: Invalid File format

```
    fn setup_zkey(&self) -> Result<(), Box<dyn Error>> {
        info!("Setting up zkey ...");

        let setup_command = format!(
            "snarkjs groth16 setup circuits/{name}/{name}.r1cs circuits/setup/pot12_final.ptau circuits/{name}/{name}_0000.zkey",
            name = self.circuit_name
        );
        info!(" setup_command {:?}", setup_command);

        self.run_command(&setup_command)?;

        info!("Zkey Generated.");
        Ok(())
    }

```

resolve:
circuit was too big for this power of tau ceremony.