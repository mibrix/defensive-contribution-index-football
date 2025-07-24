Football Analytics: Unveiling Defensive Contribution with DCI
This project introduces the Defensive Contribution Index (DCI), a cutting-edge measurement designed to give a clearer and more complete picture of how well a soccer player defends. Instead of just counting defensive actions, the DCI shows how effective these actions are at stopping the opposing team from scoring.

1. Introduction
The Defensive Contribution Index (DCI) is a new way to evaluate a player’s defensive performance in soccer. Traditional stats often just count tackles or clearances. The DCI goes a step further by looking at how well these actions actually prevent the other team from getting dangerous scoring chances. This helps scouts and analysts get a much better, more objective view of a player’s true defensive impact on the field.

2. What is the DCI?
In soccer, players make many defensive moves like tackles, blocks, interceptions, and clearances. The DCI isn't just about how many of these actions a player makes, but also how good they are. Specifically, it measures how much a defensive action reduces the chance that the opposing team will create a dangerous scoring opportunity.

To do this, the DCI uses detailed match data and focuses on two key aspects:

The quantity of defensive actions: How many tackles, blocks, etc., a player performs.

The quality of these actions: How much each action reduces the opponent's threat.

Simply put, the DCI tells us how much a player helps prevent the opposing team from scoring, by combining both how often they defend and how effective those defenses are.

3. How is it Calculated?
The DCI is calculated using detailed data from every event that happens during a game. Here’s how we compute the DCI:

Finding Defensive Actions: First, we identify all defensive actions by a player. These include tackles, various duels (like fighting for the ball on the ground or in the air), interceptions (cutting off passes), clearances (kicking the ball away from danger), and blocks (stopping shots or passes). We only count actions that happen in the player's defensive third of the field, as these are usually the most critical for preventing goals.

Measuring Impact on Expected Threat (xT): Next, we figure out how much each defensive action changes the "danger level" (or threat) posed by the opponent. We do this by calculating the Expected Threat (xT) both before and after the defensive action.

xT Before: This is our estimate of how dangerous the opponent's attack was just before the defensive action. It's calculated by combining two things:

The probability that this specific attacking possession would lead to a shot.

The expected goal value of a shot taken from that exact location, viewed from the opponent's attacking perspective.

xT After: This is our estimate of how dangerous the opponent's attack still is right after the defensive action.

If the defensive action completely stops the opponent's attack (e.g., the ball goes out of bounds, or the defending team wins possession), then the xT After is zero.

If the opponent keeps the ball, we estimate the xT of their next two touches.

If, unfortunately, the defensive action directly leads to an own goal, the xT After is considered as high as the xT Before, meaning the action didn't reduce the threat.

Calculating the Difference: For every defensive action, we subtract the "xT After" from the "xT Before" (xT_before - xT_after). A larger positive difference means the defensive action was more valuable because it significantly reduced the opponent's threat. This difference is the "threat reduction" for that action.

Combining Results: Finally, the DCI is calculated by adding up the total number of defensive actions and the total threat reduction caused by those actions. This gives us a single score for each player.

The formula for DCI is:

DCI=α×total defensive actions+β×total xT difference
Here:

total defensive actions is the sum of all tackles, duels, interceptions, clearances, and blocks/saves a player made.

total xT difference is the sum of the "threat reduction" values for all of a player's defensive actions.

α=0.01 and β=1.0 are weighting factors. They ensure that both making many defensive actions (quantity) and making highly impactful ones (quality) contribute appropriately to a player's overall DCI score.

4. Assumptions Behind the DCI
Like any statistical measure, the DCI relies on certain assumptions:

All Defensive Action Types Contribute: While their impact is measured, all types of defensive actions (tackles, blocks, clearances, etc.) are initially counted in the "quantity" part of the DCI.

Threat Reduction is the Goal: The main idea is that a defensive action's value comes from how much it lowers the opponent's chance of scoring. Actions that stop the ball from moving into dangerous areas are seen as more valuable.

Own Goals Are Not Positive: If a defensive action accidentally leads to an own goal, it won't add positively to the DCI. In fact, it's treated as if no threat was reduced, or even as a negative outcome.

5. Why is the DCI Useful for Scouts?
For scouts, the DCI offers a powerful way to objectively compare how well players defend. Traditional stats often don't show the full impact of defensive actions because they don't consider where or when these actions happened, or how much danger they truly stopped. The DCI provides a much fuller picture by showing how effectively a player actually reduces the opposition’s chances of scoring.

Additionally, the DCI is adjusted to a "per 90 minutes" basis. This means that players who play different amounts of time (e.g., a starter vs. a substitute) can be compared fairly, as their contributions are scaled to what they would be over a full game. This standardization allows for direct and meaningful comparisons across all players, regardless of their playing time.

6. Results & Insights
The DCI was calculated for players across five major European leagues (England, Spain, Germany, Italy and France) during the 2017/2018 season. From this analysis, the top 20 players for DCI per 90 minutes in each league were selected for closer examination.

I specifically looked for younger talents (players aged 28 or less in June 2018) who ranked highly in DCI. I then checked if their market value (from Transfermarkt) significantly increased after the 2017/2018 season. The "Difference (Formatted)" column in the table below shows this increase, from their value in 2018 to their highest value later in their career.

The findings for these promising young defensive players were very positive:

Average expected profit from a randomly selected player younger than 29: €7.3 million

Chance of making a profit from a randomly selected player younger than 29: 65.08%

Chance of at least breaking even (not losing value) from a randomly selected player younger than 29: 87.30%

These results suggest that the DCI can be a valuable tool for identifying high-potential defensive players who are likely to see significant increases in their market value.

Here are the top ten players from this analysis, ranked by how much their career market value increased:

Player Name

Value End 2017/18 Season

Age End 2017/18 Season

Highest Value After

Difference (Formatted)

Rank of DCI in League

Jules Koundé

€7,000,000

19

€65,000,000

€58.0m

17

Diego Carlos

€10,000,000

25

€50,000,000

€40.0m

4

Aaron Wan-Bissaka

€1,000,000

20

€40,000,000

€39.0m

8

Clément Lenglet

€25,000,000

22

€60,000,000

€35.0m

18

Joachim Andersen

€1,500,000

22

€35,000,000

€33.5m

8

Manuel Akanji

€22,000,000

22

€45,000,000

€23.0m

16

Berat Djimsiti

€1,000,000

25

€22,000,000

€21.0m

9

Benjamin Pavard

€30,000,000

22

€50,000,000

€20.0m

19

Philipp Lienhart

€2,500,000

21

€20,000,000

€17.5m

1

Lewis Dunk

€10,000,000

26

€27,000,000

€17.0m

2

The model successfully identified players who made a huge breakthrough later in their careers, such as Jules Koundé, Aaron Wan-Bissaka, Diego Carlos, and Clément Lenglet, demonstrating the DCI's potential as a powerful scouting tool.

🤖 Models Used
The core of the analytics relies on XGBoost, a powerful and efficient machine learning algorithm. I train two distinct XGBoost models:

A shot probability model (a classifier) that predicts the likelihood of a possession ending in a shot based on the positional data of individual actions.

An Expected Goals (xG) model (a regressor) that predicts the probability of a shot resulting in a goal based on its location.

These pre-trained models are then used to calculate the xT and defensive contribution metrics across all events.

📊 Data Source
This project utilizes publicly available event data from Wyscout, which provides detailed information on various on-ball actions (passes, shots, dribbles, duels, etc.) during football matches, including their start and end coordinates.

📄 License
This project is open-source and available under the MIT License.
