# Controller Design — Relay ABS (Final)

## Why relay ABS?
ABS is inherently hybrid: apply / hold / release based on slip thresholds. Relay ABS is robust to:
- nonlinear μ(λ)
- discontinuous λ when v→0
- actuator saturation

---

## Tuning Parameters
- λ_low  : lower slip threshold (e.g., 0.10)
- λ_high : upper slip threshold (e.g., 0.20)
- Tb_rate_up : how fast brake torque increases [N·m/s]
- Tb_rate_dn : how fast brake torque decreases [N·m/s]
- Tb_max : maximum allowable brake torque

---

## Expected Behavior
- λ rises during braking, enters band
- controller cycles between increase/release
- v and Rω remain near each other (wheel not fully locked)
- Fx fluctuates around peak friction region

---

## Recommended Scopes
- λ
- v and Rω (same scope)
- Tb_cmd
- Fx
- ω
