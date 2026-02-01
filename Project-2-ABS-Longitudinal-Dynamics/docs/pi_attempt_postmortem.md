# PI Attempt Postmortem — Why PI ABS Failed (In This Project)

This section documents the PI ABS experiment and why it was not stable/reliable without additional architecture.

---

## What was implemented
- error: e = λ_ref − λ
- PI: u = Kp*e + Ki*∫e
- rate limit + integration to Tb_cmd
- saturation on Tb_cmd

---

## Symptoms observed
- λ spikes to 1 (wheel lock) and/or collapses to 0
- Tb_cmd ramps aggressively, then collapses
- oscillations appear around transitions
- behavior becomes unpredictable near low speeds

---

## Root causes (engineering reasons)
1) Slip ratio λ is discontinuous near v→0
   λ = (v - Rω)/max(v, ε) becomes sensitive when v is small.

2) Tire friction μ(λ) is highly nonlinear and peaked
   Small changes in Tb_cmd can produce large changes in λ.

3) Saturation + integral windup
   When Tb_cmd saturates, the integral keeps accumulating → overshoot and instability.

4) Hybrid nature of ABS
   Real ABS is switching control, not pure linear PI.

---

## What would be required to make PI work
- Slip filtering (low-pass on λ)
- Low-speed handling (disable ABS or redefine slip below threshold speed)
- Anti-windup for integral term (clamping/back-calculation)
- Gain scheduling vs speed and estimated μ
- Wheel speed observer / smoothing

Conclusion: PI ABS was not pursued further because the relay ABS is the correct robust baseline for this project scope.
