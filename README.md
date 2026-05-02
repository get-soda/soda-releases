# soda-releases

Public distribution channel for the [Soda](https://www.getsoda.app) company brain app. For questions or feedback please visit the [Soda community Reddit channel](https://www.reddit.com/r/SodaCommunity/)

## Layout

```
soda-releases/
├── appcast.xml            # Sparkle feed, regenerated on every release
└── releases/
    ├── Soda-1.0.0.zip     # Signed + notarized + stapled app bundle
    ├── Soda-1.1.0.zip
    ├── Soda-1.1.0.delta   # Binary delta from 1.0.0 → 1.1.0 (auto-generated)
    └── Soda-1.1.0.html    # Optional release notes (linked from appcast)
```
