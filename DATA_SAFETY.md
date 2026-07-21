# Play Console — Data Safety Form Answers (Retro Rumble)

This is the local‑only v1 build: Play Games sign‑in and cloud save are disabled, and there
are no ads, analytics, or crash‑reporting SDKs. Copy these answers into
Play Console → App content → Data safety.

## Data collection & sharing
- **Does your app collect or share any of the required user data types?** → **No.**

**Rationale (keep for your records):** The developer collects nothing. Everything is stored
on the device. The only two paths that move data off the device are both **user‑initiated
actions**, which Google's Data Safety guidance does not count as collection or sharing by the
app:
1. **Bluetooth versus** — when the user chooses to host/join a local match, their chosen
   display name is sent device‑to‑device to the nearby player they selected. Nothing goes to
   the developer or any server.
2. **Export save / share** — the OS share sheet, invoked only when the user taps it, sends
   data to whatever app the user picks.

There is no advertising ID access, no third‑party analytics, no account system.

## Other Data Safety questions
- **Is all of the user data collected by your app encrypted in transit?** → Not applicable
  (no data is collected/transmitted to the developer).
- **Do you provide a way for users to request that their data be deleted?** → Data is stored
  only on the device; uninstalling the app or clearing storage removes it. (In‑app: Settings
  → reset progress.)
- **Advertising ID:** Not used / not requested.

## Verify before submitting
- Confirm the built app bundle's merged manifest contains **no**
  `com.google.android.gms.games.APP_ID` and **no** `com.google.android.gms.permission.AD_ID`.
- Only the Bluetooth/Nearby + legacy location permissions should be present (for local versus).

---

## FUTURE: if cloud save (Play Games) is re‑enabled

If you later ship the opt‑in Play Games cloud save, the answers change to:
- Collects/shares data → **Yes**.
- Data types: **App activity** (game progress) and a **Name** (the self‑set display name),
  uploaded to the player's Google Play Games Saved Games.
- Collection is **optional** (off by default), not shared with third parties, not used for
  tracking. Encrypted in transit (Google's SDK). Add a Play Games sign‑in disclosure to the
  privacy policy and configure a Play Games Services project + OAuth in the Console.
