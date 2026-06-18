# circas — sleep for sunrise, work for four hours

One screen. Shows today's date + sunrise, one checkbox **did 4 hours of deep work**, a rolling 7-dot row, and a quiet personal best. Operationalizes your oldest life-rule into one daily checkable bit.

- **No backend, no auth, no network call.** State in `localStorage` (`circas` → `{v:1, handle, days:{}, bestRun}`).
- **There is no streak object** — `days` is just a set of done-dates, so there is literally nothing that can hit zero. A miss is an absent date that scrolls off the 7-dot row in a week. The longest run shows only as a silent "best run so far", never as something you're "currently risking". The copy never scolds.
- The checkbox is a one-way latch, **today only** — no backfilling past days (that's the road to a calendar, a heatmap, a streak-repair economy).

## edit before deploy
`SUNRISE` is a hard-coded placeholder (`05:41`) at the top of the `<script>`. Set it for your city. The real sunrise API is a deliberate v1 cut (it returns UTC and needs a timezone conversion that would eat your Saturday for one decorative number).

## what's intentionally NOT here (v0 cuts)
live countdown / 4-hour "window" gating · the second "woke for sunrise?" bit · the real sunrise API + offline cache · `?share` view · sync · any visible streak number · editing past days · notifications.

## deploy
```
gh repo create neoselfy/circas --public --clone
# copy index.html in
git add -A && git commit -m "circas v0" && git push
# github → Settings → Pages → main / root → enable  →  https://neoselfy.github.io/circas
```

## the accountability
Text one human the live link: *"this is the thing. i tap it after my four hours. watch the dots."* Their reply is the feature.

## shipped =
**7 consecutive days** each holding a `true`, every one tapped in the live app (not devtools) **and** the link sent to one human who replied they're watching.
