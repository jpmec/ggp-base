GENERAL GAME PLAYING BASE PACKAGE
=================================

Application Suite for the General Game Playing Project;
- A GUI-based GameKiosk        (for playing human-vs-computer matches)
- A GUI-based GamePlayer       (for running computer players)
- A GUI-based GameServer       (for hosting matches)
- A GUI-based GDLValidator     (for validating game rulesheets)

Support code for the above.


QUICK START GUIDE
-----------------

Getting started is as simple as writing a new player that inherits from the
StateMachineGamer class. StateMachineGamer is based on the state machine view
of general game playing, in which playing a game is represented as proceeding
through a state machine. The underlying state machine, which you can access via
getStateMachine() when inheriting from StateMachineGamer, provides methods that
you can use to investigate the game being player:

+ Each game has a starting state.
  - getInitialState() is the starting state.

+ Each state has legal moves for every player.
  - getLegalMoves(state, role) are the legal moves for <role> in <state>.

+ Some states are terminal, and in those states "goal" values are defined 
for every player, indicating whether they won or lost.
  - isTerminal(state) indicates whether a state is terminal.
  - getGoal(state, role) is the goal value for <role> in <state>.

+ Given a legal move for each player, you can transition from one state to
the next state, after the players make their respective moves.
  - getNextState(state, moves) is the result of making <moves> at <state>.

A simple Prover-based state machine implementation is included in GGP Base,
so you don't need to worry about the details of converting a game description
into a state machine. To write a gamer based on StateMachineGamer, derive your
class from players.gamer.statemachine.StateMachineGamer. Applications like the
PlayerPanel should automatically recognize your new class and it should appear
in their lists of available players right away.

For examples of simple players, see src/player/gamer/statemachine/reflex,
where two extremely simple "reflex-based" players are included: LegalGamer and
RandomGamer. LegalGamer always chooses the first legal move available, and the
RandomGamer always chooses a random legal move.


MISC NOTES
----------

+ This is the 4/1/2010 release of GGP code for CS227B, compiled and maintained
  by Sam Schreiber with help and support from Ethan Dreyfuss, Eric Schkufza,
  Keith Schwarz, Steven Bills, and Mike Mintz.

+ This project is licensed under the New BSD License. Licensing information for
  the project can be found in the licenses/LICENSE file. Licensing information
  for the included external libraries can be found in the licenses/ directory.

