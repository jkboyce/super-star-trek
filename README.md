One of my earliest memories of computer games was [Star Trek](https://en.wikipedia.org/wiki/Star_Trek_(1971_video_game)). Before I ever owned a microcomputer, I played Star Trek on a [DEC PDP-11](https://en.wikipedia.org/wiki/PDP-11) timeshare system that my uncle had access to. He had a line printer terminal (basically a terminal with a printer instead of a CRT screen) with an acoustic modem coupler that fit the [AT&T phones](https://en.wikipedia.org/wiki/Princess_telephone) of the day. We would dial in to the PDP-11, listen for the grinding noise of the modem connection, shove the handset into the coupler (careful to get the right orientation), and Voila! Like magic the printer would start printing out text. The PDP-11 ran an operating system called [RSTS 7.0](https://en.wikipedia.org/wiki/RSTS/E). That's where I got my first experience with BASIC programming, in between games of Star Trek.

This is a Python port I did of the most popular version, called Super Star Trek and published in the book _Basic Computer Games_ (1978) by Dave Ahl. This port has identical gameplay to the original, and I've been careful to exactly reproduce all output and text formatting to give the authentic retro experience. The game is simple but fun and challenging even today.

For the port I chose a very direct style of translation to preserve as much of the charm of the original BASIC as I could. In the course of porting I discovered and fixed a few bugs in the [original code](orig/superstartrek.bas), as commented in the Python version. In the original they are at:
- line `440`: `B9` should be initialised to 0, not 2
- line `4410`: `D(7)` should be `D(6)`
- lines `8310`,`8330`,`8430`,`8450`: Division by zero is possible

See also:
- _Basic Computer Games_ book: [Annarchive](https://annarchive.com/files/Basic_Computer_Games_Microcomputer_Edition.pdf#page=172), [Atari Archives](https://www.atariarchives.org/basicgames/showpage.php?page=157)
- BASIC source: [Vintage Basic](http://www.vintage-basic.net/games.html)

# Super Star Trek

_Note: The text below is the game's introduction in _Basic Computer Games_, written by Dave Ahl._

## Brief History
Many versions of Star Trek have been kicking around various college campuses since the late sixties. I recall playing one at Carnegie-Mellon Univ. in 1967 or 68, and a very different one at Berkeley. However, these were a far cry from the one written by Mike Mayfield of Centerline Engineering and/or Custom Data. This was written for an HP2000C and completed in October 1972. It became the “standard” Star Trek in February 1973 when it was put in the HP contributed program library and onto a number of HP Data Center machines.

In the summer of 1973, I converted the HP version to BASIC-PLUS for DEC’s RSTS-11 compiler and added a few bits and pieces while I was at it. Mary Cole at DEC contributed enormously to this task too. Later that year I published it under the name SPACWR (Space War — in retrospect, an incorrect name) in my book _101 Basic Computer Games_. It is difficult today to find an interactive computer installation that does not have one of these versions of Star Trek available.

## Quadrant Nomenclature
Recently, certain critics have professed confusion as to the origin on the “quadrant” nomenclature used on all standard CG (Cartesian Galactic) maps. Naturally, for anyone with the remotest knowledge of history, no explanation is necessary; however, the following synopsis should suffice for the critics:

As every schoolboy knows, most of the intelligent civilizations in the Milky Way had originated galactic designations of their own choosing well before the Third Magellanic Conference, at which the so-called “2⁶ Agreement” was reached. In that historic document, the participant cultures agreed, in all two-dimensional representations of the galaxy, to specify 64 major subdivisions, ordered as an 8 x 8 matrix. This was partially in deference to the Earth culture (which had done much in the initial organization of the Federation), whose century-old galactic maps had always shown 16 major regions named after celestial landmarks divided into four “quadrants,” designated by ancient “Roman Numerals” (the origin of which has been lost).

To this day, the official logs of starships originating on near-Earth starbases still refer to the major galactic areas as “quadrants.”

The relation between the Historical and Standard nomenclatures is shown in the simplified CG map below.

|   | 1            | 2  | 3   | 4  | 5          | 6  | 7   | 8  |
|---|--------------|----|-----|----|------------|----|-----|----|
| 1 |    ANTARES   |    |     |    |   SIRIUS   |    |     |    |
|   | I            | II | III | IV | I          | II | III | IV |
| 2 |     RIGEL    |    |     |    |    DENEB   |    |     |    |
|   | I            | II | III | IV | I          | II | III | IV |
| 3 |    PROCYON   |    |     |    |   CAPELLA  |    |     |    |
|   | I            | II | III | IV | I          | II | III | IV |
| 4 | VEGA         |    |     |    | BETELGUESE |    |     |    |
|   | I            | II | III | IV | I          | II | III | IV |
| 5 |    CANOPUS   |    |     |    |  ALDEBARA  |    |     |    |
|   | I            | II | III | IV | I          | II | III | IV |
| 6 |    ALTAIR    |    |     |    |   REGULUS  |    |     |    |
|   | I            | II | III | IV | I          | II | III | IV |
| 7 | SAGITTARIOUS |    |     |    |  ARCTURUS  |    |     |    |
|   | I            | II | III | IV | I          | II | III | IV |
| 8 |    POLLUX    |    |     |    |    SPICA   |    |     |    |
|   | I            | II | III | IV | I          | II | III | IV |

## Super Star Trek† Rules and Notes

1. OBJECTIVE: You are Captain of the starship “Enterprise”† with a mission to seek and destroy a fleet of Klingon† warships (usually about 17) which are menacing the United Federation of Planets.† You have a specified number of stardates in which to complete your mission. You also have two or three Federation Starbases† for resupplying your ship.

2. You will be assigned a starting position somewhere in the galaxy. The galaxy is divided into an 8 x 8 quadrant grid. The astronomical name of a quadrant is called out upon entry into a new region. (See “Quadrant Nomenclature.”) Each quadrant is further divided into an 8 x 8 section grid.

3. On a section diagram, the following symbols are used:
    - `<*>` Enterprise
    - `†††` Klingon
    - `>!<` Starbase
    - `*`   Star

4. You have eight commands available to you (A detailed description of each command is given in the program instructions.)
    - `NAV` Navigate the Starship by setting course and warp engine speed.
    - `SRS` Short-range sensor scan (one quadrant)
    - `LRS` Long-range sensor scan (9 quadrants)
    - `PHA` Phaser† control (energy gun)
    - `TOR` Photon torpedo control
    - `SHE` Shield control (protects against phaser fire)
    - `DAM` Damage and state-of-repair report
    - `COM` Call library computer

5. Library computer options are as follows (more complete descriptions are in program instructions):
    - `0` Cumulative galactic report
    - `1` Status report
    - `2` Photon torpedo course data
    - `3` Starbase navigation data
    - `4` Direction/distance calculator
    - `5` Quadrant nomenclature map

6. Certain reports on the ship’s status are made by officers of the Enterprise who appears on the original TV Show—Spock,† Scott,† Uhura,† Chekov,† etc.

7. Klingons are non-stationary within their quadrants. If you try to maneuver on them, they will move and fire on you.

8. Firing and damage notes:
    - Phaser fire diminishes with increased distance between combatants.
    - If a Klingon zaps you hard enough (relative to your shield strength) he will generally cause damage to some part of your ship with an appropriate “Damage Control” report resulting.
    - If you don’t zap a Klingon hard enough (relative to his shield strength) you won’t damage him at all. Your sensors will tell the story.
    - Damage control will let you know when out-of-commission devices have been completely repaired.

9. Your engines will automatically shut down if you should attempt to leave the galaxy, or if you should try to maneuver through a star, or Starbase, or—heaven help you—a Klingon warship.

10. In a pinch, or if you should miscalculate slightly, some shield control energy will be automatically diverted to warp engine control (if your shield are operational!).

11. While you’re docked at a Starbase, a team of technicians can repair your ship (if you’re willing for them to spend the time required—and the repairmen _always_ underestimate…)

12. If, to same maneuvering time toward the end of the game, you should cold-bloodedly destroy a Starbase, you get a nasty note from Starfleet Command. If you destroy your _last_ Starbase, you lose the game! (For those who think this is too a harsh penalty, delete line 5360-5390, and you’ll just get a “you dumdum!”-type message on all future status reports.)

13. End game logic has been “cleaned up” in several spots, and it is possible to get a new command after successfully completing your mission (or, after resigning your old one).

14. For those of you with certain types of CRT/keyboards setups (e.g. Westinghouse 1600), a “bell” character is inserted at appropriate spots to cause the following items to flash on and off on the screen:
    - The Phrase “\*RED\*” (as in Condition: Red)
    - The character representing your present quadrant in the cumulative galactic record printout.

15. This version of Star Trek was created for a Data General Nova 800 system with 32K or core. So that it would fit, the instructions are separated from the main program via a CHAIN. For conversion to DEC BASIC-PLUS, Statement 160 (Randomize) should be moved after the return from the chained instructions, say to Statement 245. For Altair BASIC, Randomize and the chain instructions should be eliminated.

† Designates trademark of Paramount Pictures Corporation. Used by permission of Paramount Pictures Corporation.
