# Open Source Fractal

By Canto Lab on TradingView.

A from-scratch Pine Script v6 implementation of the Fractal Model concept, as publicly taught by ttrades and toodegrees. This is an independent, open source tool built for personal study and for anyone who does not want to pay a monthly fee to plot a C2 sweep, a CISD level, and a box.

Currently missing SMT. I'll be adding it soon.

## Disclaimer

I do not recommend trading this strategy as is. Read the rest of this README before you download the indicator for better understanding.

## How this was built

This script was written independently, from scratch, based on publicly available educational content explaining the Fractal Model concept (YouTube explanations, public discussion of the methodology,CRT/MXMM explanations etc). No proprietary source code from any commercial indicator was accessed, copied, or referenced in building this. The logic, structure, and code here are my own.

## Why I'm saying that

Over the last year I've watched a pattern repeat across this space: someone repackages this same model under a new name, adds a logo, and sells access to it. The pitch is always some version of the same idea: a C2 sweep followed by a CISD tells you where price is going next. Once you strip away the branding, that claim does not hold up.

There is nothing about a C2 pattern by itself that has predictive power over direction. If you backtest C2 setups in isolation, across enough sample size, they are not profitable. That's not a subjective take, it's just what happens when you actually run the numbers instead of screenshotting the fifteen setups that worked this month.

The usual response to that is "you need a daily bias" or "you need to filter by time of day." Fine, add those filters. C2 setups still don't work on their own once you control for that. And here's the part that actually matters: if your daily bias is genuinely accurate, you don't need the C2 setup at all. You would already be profitable trading the bias by itself. Dropping down to the LTF to wait for a sweep and a CISD doesn't add edge, it just adds entries that feel more precise because you have a box drawn on your chart.

Trading with the higher timeframe trend can work. That's not controversial, it's basically trend following. But a C2 setup is not a trend identification tool. It's a local structure shift after a liquidity grab. It doesn't tell you anything about where the broader trend is going, which is exactly why it fails as a standalone system.

## The part nobody talks about

The strategy itself is very mechanical. Anyone who has tried to turn this into an indicator has already written the exact rules a backtest or an automated strategy would need. The C2 trigger, the CISD confirmation, the invalidation, all of it is sitting right there in the logic. Automating it isn't complicated. Building the indicator is already most of the way there.

The last step rarely gets taken, and I think the reason is simple. Automating it means running it on real data across real time and publishing the win rate and the analytics, and those numbers don't tend to hold up to the expectations that get sold around this concept. As long as it stays discretionary, there's always an out. If a setup doesn't work, that's on the trader for taking a bad one, for not filtering it right, for not having enough discipline that day. Psychology becomes the scapegoat. An automated version doesn't get that excuse. It just does what the rules say, and the equity curve either works or it doesn't.

## Advanced financial explanation on why technical patterns don't work (EMH)

This is basically a live case study for the Efficient Market Hypothesis. Prices already reflect all publicly available information, including the fact that a pattern like a liquidity sweep followed by a reversal candle exists and is being watched by enough participants. Any repeatable, purely price based pattern that requires no proprietary information should get arbitraged away as more people trade it, because the moment enough capital tries to front run the same visual setup, the setup itself changes the price action it depends on.

A C2 setup, structurally, is just a pinbar or reversal candle formation with extra steps. Reversal candle patterns have been studied for decades in technical analysis literature, and what shows up in that research fairly consistently is a small statistical edge at best, usually not enough to survive transaction costs, slippage, and the psychological cost of managing a discretionary system in real time. Any minor edge that does exist is closer to a liquidity or market microstructure effect (stop hunts clustering around obvious swing points) rather than a genuine directional signal, and that effect is inconsistent and gets thinner the more popular the pattern becomes.

### So why do some people still hit a payout trading this?

Because a pinbar or a sweep and reclaim does carry some short term information, it's not zero. Combine that with variance, a large enough sample of traders all taking similar setups, and normal survivorship bias, and some of them are going to pass an evaluation, and some will even put up large numbers in the short term. That's expected under pure chance too. It's not evidence the model has an edge, it's evidence that enough people tried it.

Given a long enough timeline, the same accounts trend back toward negative returns, and the ones that don't blow up still tend to underperform something as simple as buying and holding the S&P 500. If your baseline expectation walking into this is ten percent a month, consistently, that's not a realistic target for any strategy, let alone one built on a pattern with this little standalone edge.

## Why open source

None of this needed to be a paid product. It's a handful of drawing objects and some conditional logic on top of an HTF security call. I've also seen versions of this concept get built out into two thousand to four thousand line scripts, often in ways that suggest the author either didn't fully understand the underlying logic or leaned heavily on AI tooling without knowing how to structure or optimize repeatable code. This repo is my attempt at a clean, minimal, properly organized version of the same tool, for anyone who wants to study it or build on top of it for free.

## Features

- Auto or custom LTF and HTF fractal alignment
- C2 sweep detection with bullish and bearish setups
- Early CISD and confirmed CISD levels
- Standard deviation projections off the CISD
- HTF candle preview with open line, O/C time markers, and L/H lines
- Configurable history depth for setups and early CISD lines
- On chart dashboard showing alignment, bias, and timeframe validity

## Installation

1. Open TradingView and go to the Pine Editor.
2. Create a new indicator and paste in the contents of `openSourceFractal.pine`.
3. Save and add it to your chart.


## Contributing

SMT is on the roadmap. Pull requests welcome, especially if you have a clean way to bring in correlated pairs without bloating the script.

## License

MIT. Do whatever you want with it
