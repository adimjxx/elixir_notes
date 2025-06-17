```json
{
    // ZIG :start
    "zig.zls.enabled": "on",
    // ZIG :end
    // ELIXIR :start
    "elixirLS.suggestSpecs": false, // disable automatic suggestions for function specs
    "elixirLS.dialyzerEnabled": true, // tool for static analysis of code
    "elixirLS.signatureAfterComplete": false, // disable showing function signatures after auto-completion
    "elixirLS.fetchDeps": false, // fetch project dependencies
    "[elixir]": {
        "editor.formatOnSave": true, // automatically format code on save
        "editor.defaultFormatter": "JakeBecker.elixir-ls" // format with this formatter
    },
    // ELIXIR :start
    // EDITOR :start
    "security.allowedUNCHosts": [
        "wsl.localhost"
    ],
    "editor.minimap.renderCharacters": false,
    "editor.minimap.side": "left",
        "editor.fontFamily": "\"3270 Nerd Font Mono\", Consolas, 'Courier New', monospace",
    "editor.fontSize": 18,
    // EDITOR :end
}
```