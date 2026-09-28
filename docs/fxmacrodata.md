# FXMacroData integration helper

`src/Share/FxMacroData.hpp` provides a small C++ URL builder for FXMacroData
REST endpoints. It is header-only so it can be used with the HTTP transport
already selected by a WonderTrader deployment.

```cpp
#include "Share/FxMacroData.hpp"

wt::FxMacroDataUrlBuilder fxmd("YOUR_API_KEY");
std::string url = fxmd.forex("eur", "usd", {{"limit", "100"}, {"offset", "0"}});
```

List endpoints (announcements, predictions, forex, COT, commodities) return
20 rows by default and at most 100 per request, newest first. To read a longer
history, request `limit=100` and repeat with `offset` set to
`pagination.next_offset` while `pagination.has_more` is true.

The helper covers macro catalogues, announcements, release calendars,
predictions, FX history, COT positioning, commodities, market sessions, risk
sentiment, and press releases.
