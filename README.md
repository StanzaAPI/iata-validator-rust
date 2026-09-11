# IATA Air Cargo AWB & Aviation Validator — Rust Client Crate

[![Crates.io](https://img.shields.io/crates/v/stanzaapi-iata-validator.svg)](https://crates.io/crates/stanzaapi-iata-validator)
[![Documentation](https://docs.rs/stanzaapi-iata-validator/badge.svg)](https://docs.rs/stanzaapi-iata-validator)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Stanza API](https://img.shields.io/badge/Powered%20by-Stanza-blue)](https://stanzaapi.com)

> Validate IATA Resolution 600a Air Waybills (11-digit MOD-7), e-tickets, and airline accounting prefixes in sub-5ms.

Official high-performance, asynchronous Rust client library for **IATA Air Cargo AWB & Aviation Validator**, built on the [Stanza Micro-API Network](https://stanzaapi.com). Uses pure Rustls TLS (zero C/OpenSSL dependencies) and Tokio for maximum concurrency and safety.

* 🌐 **Online Interactive Sandbox:** [Test your inputs live](https://stanzaapi.com/tools/iata-validator)
* 📚 **API Reference & Schemas:** [View documentation on Stanza](https://stanzaapi.com/tools/iata-validator)
* ⚡ **Platform Overview:** [Explore the Stanza Developer Network](https://stanzaapi.com)

---

## 📦 Installation

Add to your `Cargo.toml`:

```toml
[dependencies]
stanzaapi-iata-validator = "1.0.0"
tokio = { version = "1.0", features = ["full"] }
```

Or use `cargo add`:

```bash
cargo add stanzaapi-iata-validator
```

---

## 🚀 Quickstart

```rust
use stanzaapi_iata_validator::IataValidatorClient;

#[tokio::main]
async fn main() -> Result<(), Box<dyn std::error::Error>> {
    // Reads STANZA_API_KEY from environment automatically
    // Public edge default: https://api.stanzaapi.com/iata-validator
    let client = IataValidatorClient::new(None, None);

    let response = client.validate("020-12345675").await?;

    if response.success {
        println!("Verification Success: {:?}", response.data);
    } else {
        eprintln!("Validation Error: {:?}", response.error);
    }

    Ok(())
}
```

---

## 📄 Example Response

```json
{
  "success": true,
  "data": {
    "valid": true,
    "prefix": "020",
    "airline": "Lufthansa Cargo",
    "serial_number": "1234567",
    "check_digit": 5
  }
}
```

---

## 🔗 Useful Links

* [IATA Air Cargo AWB & Aviation Validator Interactive Sandbox](https://stanzaapi.com/tools/iata-validator)
* [Stanza Developer Directory](https://stanzaapi.com)
* [Source Code & Issue Tracker](https://github.com/StanzaAPI/iata-validator-rust)

## 📄 License

MIT © Stanza — Powered by [Stanza](https://stanzaapi.com).
