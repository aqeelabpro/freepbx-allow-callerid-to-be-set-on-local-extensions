
# Ensure The CallerID is Present When a Call is Dialed

Sometimes, ensuring that the `CallerID` we want is present and shown to the callee when making a call using Asterisk is necessary.

---

## Asterisk `CALLERID()` Function

The `CALLERID()` function gets or sets `Caller*ID` data on the channel. By default, it uses the channel being called. For example, if extension `2000` is dialed from user `3000`, the `CallerID` is set to `3000` by default unless an optional `CallerID` is specified.

---

### `pres` Field

The `pres` field gets or sets a combined value for `name-pres` and `num-pres`.

---

### Allowable Values for `name-charset`

1. `unknown` - Unknown  
2. `iso8859-1` - ISO8859-1  
3. `withdrawn` - Withdrawn  
4. `iso8859-2` - ISO8859-2  
5. `iso8859-3` - ISO8859-3  
6. `iso8859-4` - ISO8859-4  
7. `iso8859-5` - ISO8859-5  
8. `iso8859-7` - ISO8859-7  
9. `bmp` - ISO10646 BMP String  
10. `utf8` - ISO10646 UTF-8 String  

---

### Allowable Values for `num-pres`, `name-pres`, and `pres`

1. `allowed_not_screened` - Presentation Allowed, Not Screened.  
2. `allowed_passed_screen` - Presentation Allowed, Passed Screen.  
3. `allowed_failed_screen` - Presentation Allowed, Failed Screen.  
4. `allowed` - Presentation Allowed, Network Number.  
5. `prohib_not_screened` - Presentation Prohibited, Not Screened.  
6. `prohib_passed_screen` - Presentation Prohibited, Passed Screen.  
7. `prohib_failed_screen` - Presentation Prohibited, Failed Screen.  
8. `prohib` - Presentation Prohibited, Network Number.  
9. `unavailable` - Number Unavailable.  

---

### `CALL_QUALIFIER`

`CALL_QUALIFIER` is a special `CallerID`-related variable that enables sending the *Call Qualifier* parameter in `MDMF` (Multiple Data Message Format) `CallerID` spills.

> **Note:**  
> - This variable is not automatically set by Asterisk. It must be set manually when required.  
> - Supporting `CallerID` units display the `LDC` (Long Distance Call) indicator upon receiving this parameter.  
> - For incoming calls on `FXO` ports, the variable will be set to `1` if the Call Qualifier parameter is received.  
> - Use this option with a channel driver that allows Asterisk to generate the `CallerID` spill (currently only includes `chan_dahdi`).

---

## Syntax

```plaintext
CALLERID(datatype, CID)
```

---

### Arguments

#### `datatype`

The allowable `datatypes` are:  

- `all`  
- `name`  
- `name-valid`  
- `name-charset`  
- `name-pres`  
- `num`  
- `num-valid`  
- `num-plan`  
- `num-pres`  
- `pres`  
- `subaddr`  
- `subaddr-valid`  
- `subaddr-type`  
- `subaddr-odd`  
- `tag`  
- `priv-all`  
- `priv-name`  
- `priv-name-valid`  
- `priv-name-charset`  
- `priv-name-pres`  
- `priv-num`  
- `priv-num-valid`  
- `priv-num-plan`  
- `priv-num-pres`  
- `priv-subaddr`  
- `priv-subaddr-valid`  
- `priv-subaddr-type`  
- `priv-subaddr-odd`  
- `priv-tag`  
- `ANI-all`  
- `ANI-name`  
- `ANI-name-valid`  
- `ANI-name-charset`  
- `ANI-name-pres`  
- `ANI-num`  
- `ANI-num-valid`  
- `ANI-num-plan`  
- `ANI-num-pres`  
- `ANI-tag`  
- `RDNIS`  
- `DNID`  
- `dnid-num-plan`  
- `dnid-subaddr`  
- `dnid-subaddr-valid`  
- `dnid-subaddr-type`  
- `dnid-subaddr-odd`  

---

# Example
same => n,Set(CALLERID(pres)=allowed) ; it ensures that callerid is present and shown to user when dialed


#### `CID`

An optional `CallerID` to parse instead of using the `CallerID` from the channel.  
This parameter is only optional when reading the `Caller*ID`.  
```
