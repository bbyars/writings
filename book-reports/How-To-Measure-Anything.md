Erastosthenes (~200 BC) measured the circumference of the earth, within 3% accuracy, by reading that, on a certain day of the year, a well in a certain city showed no shadow, meaning the sun was directly overhead. He found the angle of the shadow on the same day to be 1/50 of a circle, and therefore multiplied 50 times the distance between the two cities.

Measurement doesn't need to be precise. It simply needs to reduce uncertainty.

A great place to begin with measurement is to estimate a 90% confidence interval. But its important that the 90% CI is calibrated - most people are prone to being overconfident, so a 90% CI really means that they're right maybe 7 times out of 10.

With a series of 90% CI estimates, you can run a Monte Carlo simulation, which randomly picks one of the values from the range for each variable to compute the thing you're measuring, and repeats thousands of times to generate a curve. It's important that you have an understanding of the shape of distribution of your 90% CI. A normal curve will produce different values that a uniform curve or Bernoulli (binary).

*Measurement Inversion* - in a business case, the economic value of measuring a variable is usually inversely proportional to how much measurement attention it gets. The reasons for this inversion:
* People measure what they know how to measure or what they believe is easy to measure
* People measure things likely to produce good news, especially to justify what they want to people signing the checks
* People don't know the business value of the information from a measurement, so they can't put the difficulty of measurement in context
    
It's like the drunk man who knows he lost his watch in a dark alley, but when asked why he's looking for it in the lighted street, answers, because the lighting is better.

Understanding how to measure uncertainty is the key to measuring risk. Understanding risk is key to understanding how to compute the value of information. Understanding the value of information tells us what to measure and how much effort to put into measuring it.

The early part of any measurement is usually the high-value part. When you have a lot of uncertainty, you only need a little measurment to reduce the uncertainty. When you have more certainty (a narrower CI gap), you need much more measurement to narrow the gap further.

Prefer accuracy to precision. Accuracy minimizes systemic error but allows random error. Precision does the opposite. Much better to randomly sample a small number of events than to review a large number of recorded memories of events.

How do you measure the number of fish in a lake? Biologists will catch and release, say, 1000 fish, tagging each one before releasing it. Some time later, they'll catch another 1000 fish and count the number of those tagged. Say 50 of them were tagged, or 5%. Then they'd say there are 20,000 fish in the lake (1000 is 5% of 20,000).
