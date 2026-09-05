# Current playtest

Transcript of session 2, written into the repo mid-session at the player's request,
for post-mortem analysis.

**Provenance note.** This is reconstructed from the live session context, not from a
byte-level capture. Player turns and GM prose are verbatim. Omitted: system reminders,
tool-call payloads, and the notes files' own diffs (those are in git history). GM tool
actions — oracle consultations, dice, note commits — are recorded inline in `[brackets]`
because they are the most useful evidence about whether the procedure in `CLAUDE.md` was
actually followed.

- **Date:** 2026-09-05
- **System:** ACKS II (Imperial Imprint), `acks-ii` rules skill loaded at session start
- **Where it ran:** Claude Code on the web, remote session, repo `awenonian/ACKS-1`,
  branch `claude/game-session-2-ewr0yy`
- **Opening message, verbatim:** "Hello! I'd like to resume this game with session 2!"
- **Context at session start:** Session 1 complete. Notes tree populated: CAMPAIGN,
  gm/STATE, gm/THREADS, gm/CLUES, three character files, player-facing RECORD/STATE/
  POSITIONS, and a written SESSION-02 plan. Chaos factor 5. Two clocks running.

## Log

Verbatim, in order. Not tidied afterwards.

---

**GM (turn 1) —** [read `notes/README.md`, then the full notes tree, then git log; loaded
the `acks-ii` skill; fixed a stale skill path in `CAMPAIGN.md` and committed it]

> Notes read. Before we start — give me your recap: where you think we left off, what
> Edward was in the middle of, whatever's stuck in your head from last time. Doesn't have
> to be tidy or complete; the half you remember is the half that mattered.
>
> (Standing reminder, once: any out-of-character "stop," "skip that," or "rewind" gets
> obeyed on the spot, no questions. And `log:` anything you want noted about how the game
> itself is running.)

---

**PLAYER —**

> Edward was hired to join a caravan to the borderlands, because he can read the way
> stones. When nearing an important destination, he read a way stone that was off. It
> claimed the wrong distance to nearby landmarks, and the carvings looked too unworn for
> it's ~400 year supposed age. When investigating more, he found a Zaharan stone
> underneath, and our weather witch (or something) ran off ahead without saying anything.

---

**GM —** [reconciled against notes silently; no contradictions, no absences; nothing raised]

> That matches what I've got. Nauriva — the weather-reader, second wagon. She's the one
> who rode off.
>
> ---
>
> Four hours to dawn, Edward, and you have been on your knees in the dirt for most of the
> night.
>
> The fire is coals. Somebody built it up an hour ago and nobody has since. Behind you the
> wagons make four dark shapes with the canvas gone silver-grey, and the stone stands over
> the hole you dug at its foot like a man standing over an open grave. Your hands smell of
> wet earth and torch pitch. There is a piece of roof-tile in your pocket, still cold, with
> a lip on it that says kiln and says *recent* and says so in a way that a magistrate could
> hold in his own hand and understand without knowing one letter of Auran.
>
> Kest's mattock is where you left it, leaned against the stone. Kest is asleep. So is
> everyone.
>
> Except Destrio, who is not. He is sitting on the tailgate of the lead wagon with a
> blanket round his shoulders and his boots on, which is not how a man sits when he intends
> to go back to bed, and he has been sitting there long enough to watch you finish. He has
> your written statement folded in his coat — the one you gave him, with his name under
> yours, which sets out the formula, the league discrepancy, the state of the cutting, and
> the tile.
>
> It does not mention what is under the stone. You didn't put that in.
>
> The road east goes off into the dark towards the ford. It's empty, and has been since
> Nauriva took it.
>
> What do you do?

---

**PLAYER —**

> Well, I think we have our evidence of fraud, I'm still just not sure what it means.
> Destrio wanted it in writing, and I've given it to him, and we have the tiles as easy
> proof. But why? Last session, at the end, we established that, despite the unworn
> markings, this stone is legitimate for it's age, so it was moved, not made. (And moved
> from somewhere it was protected from weather?)
> I think the best place to find more would be the next stone. If it's also wrong by a
> league, then maybe someone is attempting to extend the reach of the empire just a little.
>
> And I have no idea about the Zaharan stone. I'd like to look more into what's going on
> with that. Is it related to the fraud in any way?

---

**GM —** [oracle: "The Zaharan upright that once stood in this plinth's socket is still
findable in the immediate vicinity of the stone" — unlikely, chaos 5 → **NO** (rolled 50
vs 30). Resolved on establishment: it was carted off and reused; recorded later as being
in the waystation footings.]

> That's yours to work out. Here's what looking gets you.
>
> ---
>
> You go back down on your knees with the torch, and this time you look at the *block*, not
> the writing on it.
>
> The ground tells you first. Around the granite there is a lens of loose fill — rubble, the
> broken tile, a wedge of packed clay — and it stops. Under it and around it the earth is
> old: compacted, threaded through with fine dead root, the colour that ground goes when
> nothing has opened it in a very long time. The block sits in that. Whatever was done here
> was done to the granite. Nobody lifted the block. The block was already the hole.
>
> Second: the socket cut into its upper face is the wrong shape. It is squarer than the
> granite's foot and a good deal bigger, and the granite stands in it the way a spoon stands
> in a bucket — it is the packing that holds it plumb, not the socket. And the socket's
> inner edges are *rounded*. Not chipped, not fresh: weather-rounded, soft, the way a lip of
> stone goes when rain has been running into it for centuries. Whatever stood in it stood
> there once and was gone long, long before anybody came out here with a sledge.
>
> Third — and you have to lie flat with the torch held out sideways to see it, and your hand
> shakes — the writing has an orientation. The interdiction runs around the socket, framing
> it, and the feet of the letters point north. Which means it was cut to be read by someone
> standing on the north side, facing south. Coming down out of the high scrub, toward the
> road, toward the Empire.
>
> It does not address anyone leaving. It addresses whoever is coming back.
>
> The torch gutters. Behind you the tailgate creaks.
>
> "That's four hours in a hole," Destrio says. Not unkindly. "The paper's written. Is there
> more paper in it, or is it a different thing entirely?"
>
> He looks east, where the road is, where Nauriva went.
>
> "She said the water'd be up by second bell. If she's right we sit on the bank half a day
> and it costs us nothing but the day. If she's wrong—"
>
> He stops there. He does not finish it.

---

**PLAYER —**

> "I think it's unrelated. The previous marker before the Empire took over, I think. They
> just placed the stones in the same spot, since the landmarks were reused, is my guess."
> "If the weather's bad enough to make the ford uncrossable, we might want to be hunkered
> down for it."

---

**GM —** [no reaction to the theory's content — per `CLAUDE.md`, Destrio doesn't care about
Zaharan and says so as a trader]

> "Zaharan," Destrio says. He turns the word over like a coin he's not sure of. "Is that
> worth anything?"
>
> He doesn't wait for an answer, and he doesn't ask again. That's the whole of his interest
> in thirteen hundred years.
>
> You look up while he's thinking about it. The stars are gone out of the north — not
> clouded over that you can watch happening, just gone, a black shelf where the sky was. The
> wind has come round off your left cheek onto your right some time in the last hour and it
> has weight in it now. The air smells like wet rock.
>
> She was right. Whatever else she was.
>
> "Hunker down." Destrio says it without heat, and turns his head to take in the camp: four
> wagons, coals, scrub, the stone, the hole. Grey rock and dry watercourse for as far as the
> dark goes. "Here. No water we didn't carry, no wood we didn't carry, no wall. Two men with
> spears and neither one of them any good." He pulls the blanket up. "If we're sitting a day,
> I'd sooner sit where the sitting's finished, and there's a bank at Mirmen and hard standing
> and a man who sells fodder at a price I hate. That's still a price."
>
> He's quiet a moment.
>
> "You're going to want to walk slow tomorrow, aren't you. Counting." Not a complaint — he
> says it the way he'd note a wheel needed greasing. "You can walk slow. We're not making the
> crossing today whatever we do."
>
> Then he leans forward, elbows on his knees, and asks the question he's been sitting out here
> four hours to ask.
>
> "Say it plain, Copper. We come up on that crossing, and the man puts his hand out. What am I
> doing? Do I pay him?"

---

**PLAYER —**

> Do I know the law? Like the empire claims dominion out to 15 leagues past the landmark, and
> the stones probably have Mirmen a league short if they weren't tampered with?

---

**GM —** [character-competence knowledge, no throw: "competent character, unpressured,
ordinary task → it works." Resolved Auran boundary law on establishment.]

> You know this cold. It is the thing you were hired for, and it is the reason a man pays a
> scholar to walk beside wagons.
>
> The Empire does not claim ground by distance. There is no radius, no fifteen leagues from
> anywhere. The frontier here is a **limes** — a line surveyed once, on the ground, by men with
> rods and a commission, and then fixed in place by cut stone. The stones do not describe the
> border. In law they *are* it, in the same way a title-deed is not a description of a house.
>
> But a monument can fall, and the surveyors knew it. That is what the numbers are for. Every
> stone of a proper survey carries its distance back to the seat of that survey, so that a
> single stone standing alone in scrub can still be checked against the line that made it. This
> one says: *eleven leagues to the marker at Casra Nuvicerre.* Not Mirmen. Boundary stones point
> backward, toward the authority, never forward.
>
> And behind the stone there is a roll — a *forma*, the surveyor's own record, filed at the
> seat. For this stretch that is Casra Nuvicerre, which you walked through three days ago, and
> where the nearest magistrate with jurisdiction over bounds also sits.
>
> Where roll and monument disagree, the roll governs. That is the law and it is not ambiguous.
>
> The law also requires somebody to produce the roll, and a magistrate to hear it, and neither
> of those things is between here and the river.
>
> Destrio is still waiting. The wind has picked up.
>
> "Copper. Do I pay him?"

---

**PLAYER —**

> "My guess is this is wrong because he's trying to claim to be under Casra Nuvicerre when he
> isn't, meaning his tax is illegitimate. I'll know better if we see more stones that are also
> moved up a league."
> "That said, this is the Borderlands, and we're already 12 leagues from the nearest authority.
> So whatever the *law* is, the *rule* may be that he has more spears than us. Not paying him
> is unlikely to keep him friendly."

---

**GM —** [Destrio commits to paying — first POSITION of the session]

> "Then the answer's yes." Destrio says it flat, like a man reading a total at the bottom of a
> column. "I pay him."
>
> He doesn't sound relieved. He sits with it a moment, and then, because it is the only shape
> his mind takes:
>
> "Three sun. Then five. Then six. Then eight, in Solis. Twenty-two sun in a year off four
> wagons." He works his jaw. "And it goes up every time and every time there's a reason, and now
> you tell me the reason might not even be his to give." He pulls the blanket tighter. "I'll pay
> him. I'll pay him and I'll smile at him and I'll buy his fodder at his price. And this—" he
> touches his coat where the folded paper is "—goes to the bounds-court at Casra Nuvicerre when I
> come back west, which is the fifth week from now, and not before, because I am not turning four
> wagons round on the word of a stone."
>
> He looks at you then, properly, and there is something behind it he does not have words for and
> will not go looking for them.
>
> "He'll know we stopped. Wagons due yesterday come in today, he asks why. That's not cleverness
> on his part, that's just arithmetic." A pause. "I'd rather he asked me than found out."
>
> Then he nods at the ground behind you — at the pit you've opened at the foot of the marker,
> spoil heaped, tile in your pocket, the black Zaharan face of the plinth open to the sky for the
> first time in three hundred and eighty years.
>
> "You going to put that back?"

---

**PLAYER —**

> I probably should. It's probably vandalism or something if I don't.
> "Yeah."
> I get to work putting it back the way we found it.
> "He'll ask. We might want a story. I don't think 'We found info that will get you in trouble'
> goes over much better than 'and we're not gonna pay a few suns because of it' does."

---

**GM —** [no roll for the backfill: ordinary labour, unpressured; the concealment was moot
because Nauriva had already ridden ahead, and a roll for a moot thing "manufactures a random
chance of nothing interesting"]

> You're right to be careful, and you know exactly how right.
>
> Auran law on boundary monuments is old and it is not gentle. A *terminus* is sacred before it is
> administrative — the Empire inherited that from cults older than itself. To move one, deface one,
> or plough one out is *termini moti*, and it is not a fine. For a freeman it is loss of the land in
> dispute, twice its value, and infamy — the standing loss, no office, no oath taken as good. For a
> slave it used to be death and in the Borderlands probably still is, on whatever authority is
> nearest.
>
> Which is a thing to think about, kneeling in a hole you dug at the foot of one.
>
> So you put it back. It takes the best part of two hours with Kest's mattock and your hands: spoil
> in, packing rubble and tile back around the shaft the way it was wedged, clay trodden down, the
> turf-scraps laid over. It is not invisible. Filled ground is filled ground and any man who has dug
> a posthole would read it in a glance. But it is closed, and the marker stands as plumb as you
> found it, and when the rain comes — and it will, the first spits arrive while you're treading down
> — the rain will do what you can't.
>
> Destrio watches the last of it. Then he says, without apology:
>
> "I'll not lie to him. Not won't — *can't*. I'm no good at it, and he's had four years of practice
> at being lied to."
>
> He picks up the mattock and turns it in his hands.
>
> "So make it a story that's true."

---

**PLAYER —**

> "I got distracted by old stones. The Zaharan one, if you need specifics. Cost us a few hours,
> which cost us the crossing."
> "Though Nauvira may have already cost us any chance to keep this hidden. Reasons she might've
> run off are to do some esoteric weather reader thing, which seems unlikely, or because she was
> a spy. Seems a little odd to go through all the trouble just for us, but I don't have any
> other good stories for why she ran off."

---

**GM —** [player lands on "spy," which is correct. Not confirmed, not denied, no warmth, no
cooling. Destrio gives facts only, per his INTENTION: "I don't guess at people."]

> "I don't guess at people," Destrio says. "I'll tell you what I know and you can guess."
>
> He counts it off on the mattock handle, one knuckle at a time, the way he'd count barrels.
>
> "Third time I've hired her. Kavala to Mirmen and back, twice before, both this year. Both times
> she came to me. I never went looking." Second knuckle. "She's the best weather I've ever had on
> a wagon and she asks less than she's worth, and I've never once asked her why, because a man who
> queries a low price gets a high one." Third. "She left the money counted. Not flung down —
> *counted*, in stacks, coppers squared off, eleven days to the day. Whatever that is, it isn't
> running."
>
> He stops there and looks at you, waiting to see if you'll push it. He won't go further. He is a
> man who can hold a grievance for a year and will not hold a suspicion for a minute, and it is not
> a virtue, it's how he sleeps.
>
> Then, on the story: "That'll do. It's true and it's dull, and dull is the good part." He hefts the
> mattock. "I'll tell him I gave up the crossing for it, because I did, and I'll be sour about it,
> because I am."
>
> He hands the mattock back to Kest's wagon and adds, not looking at you:
>
> "I'd not say *Zaharan* out loud at that crossing, though. You say Zaharan to eleven men who've been
> sat on this road four years with nobody to relieve them, and half of them hear *sorcery*, and the
> half that don't will watch the half that do." A grunt. "Say old stones. Old's enough."
>
> ---
>
> The rain comes on properly at first light — not hard, steady, the kind that sets in. Camp breaks
> slowly and badly in it. By the time the wagons are moving, the marker behind you is a grey shape in
> grey water and the filled ground at its foot is already a puddle.
>
> Ahead, the road runs east into the rain, and somewhere out there is the next stone.
>
> What are you doing as you walk?

---

**PLAYER —**

> I don't think I have anything to do until we find the next stone. Hopefully we barely need to stop
> for it, just read the distance and see if it's still a league ahead.

---

**GM —** [oracle scene check, *before* narrating: "the caravan makes the league to the sixth stone in
the rain and Edward reads and paces it undisturbed" → **SCENE AS EXPECTED** (rolled 9 vs chaos 5).
The prepped short leg is delivered with no throw, per `SESSION-02.md`: "If he paces it, it is short.
No throw."]

> The road east is a made road and it holds up in the rain, which is the one mercy of the morning.
> Everything else is wet. You walk on the verge, counting.
>
> You count the way you were taught to: double-paces, a bean moved from the left pocket to the right at
> every hundred, a mark in the journal at every ten beans. A thousand double-paces to the mile. It is
> tedious and it is the only measurement a man can make with no instrument but his own legs, and yours
> are the same legs that made every other leg in the book, which is what makes the numbers comparable.
>
> Three beans short of three thousand when the stone comes up out of the rain.
>
> It stands at the tail of a low ridge where the road bends round it — a terrain point, the way they all
> are. It is grey with lichen and the top is rounded off and there is a white splash of bird lime down
> one shoulder that has been there long enough to eat into the surface. It looks like the four you read
> yesterday morning. It looks its age.
>
> The formula is the same. Same hand, same reign, same flat-tailed R.
>
> *Thirteen leagues to the marker at Casra Nuvicerre.*
>
> The ground at its foot is turf right up to the stone, grown tight against it, no packing, no rubble, no
> tile, and the weathering runs evenly all the way round the shaft and down to the grass. No stain. No
> soil-line.
>
> Your journal, then, in your own hand and your own beans:
>
> - The stone behind you says **eleven** leagues to Casra Nuvicerre.
> - This one says **thirteen**.
> - By their own numbers they stand **two leagues** apart.
> - You walked **one**.
>
> Behind you, the wagons are not stopping. Kest calls something about the fodder that the rain eats.
>
> Ahead and below, where the ridge lets you see three or four leagues of wet country, there is a seam of
> paler grey in the murk that is the Mirmen valley, and a stain of smoke over it that doesn't lift.

---

**PLAYER —**

> I'll go report this to Destrio. Kept relatively quiet. I don't want to look like I'm keeping a secret,
> but don't want to announce this.
> "Stone's now off by 2 leagues. That's two moved."
> How many leagues out is Mirmen?

---

**GM —** [player's arithmetic is wrong — the two errors have opposite signs and bracket one stone. Judged
this as character competence (Edward's own trade arithmetic), not as doing the player's inference for him,
and had Edward catch it mid-sentence]

> You fall in beside the lead wagon where the rain and the wheels make a wall around any two men walking
> close. Nobody looks up. It's the best privacy the road offers.
>
> "Stone's now off by two leagues," you start. "That's two mov—"
>
> And you stop, because it isn't, and you knew it before your mouth caught up.
>
> The errors run opposite ways. Yesterday's leg was a league too *long*; this morning's is a league too
> *short*. Two errors pointing at each other, and the thing standing between them is the one stone with the
> stained face and the soil-line and tile in its packing. This one behind you has turf grown tight to the
> shaft and no packing at all.
>
> One stone. One league. Measured twice, from both sides, by the same legs.
>
> Destrio waits out the correction without comment. When you give him the version that's true he grunts.
>
> "So it's the one. Fine. That I can hold." Rain off the brim of his hood. "Two stones moved would've meant
> a *scheme*, and schemes have more men in them."
>
> Then, to your question — he doesn't even look up, he just knows this road:
>
> "Three leagues to the crossing. Half a day in this. And the water'll be up over the stepping-stones before
> we're in sight of them, so you'll have your afternoon to be clever in."

---

**PLAYER —**

> Oh. Hm. So one stone was moved, in the middle of unimportant land? Why? To cover up the Zaharan stone? To
> cover up that someone lost number 12? It doesn't extend anyone's reach, so it can't be about the actual
> numbers.
> Which incidentally means that the guy at Mirmen isn't faking a claim, unless it very specifically was a
> claim about something at the 12th league marker, where there wasn't anything worth making a claim about.
> At least Destrio already planned on paying him...

---

**GM —** [This is the turn where the prep's geometry did not hold up, and the player found the hole. Resolved
it properly and wrote it into `gm/STATE.md` before answering: the Ulkyrean survey *overshot*, so the marker
chain is longer than the Empire and the frontier is declared at a named stone. Corrected the player's premise
because it is Edward's own professional knowledge, not an inference about the mystery.]

> You're reasoning from a premise Edward doesn't hold, and he'd catch it before the next hundred paces are
> counted.
>
> You are thinking of the chain as *the Empire* — as if the markers are the border, so shuffling one along it
> changes nothing. That isn't how this survey works, and it isn't how any frontier survey works out here.
>
> The Ulkyrean survey **overshot.** Three hundred and eighty years ago the Empire fully intended to take this
> country, and the surveyors ran their chain the whole way out along this road — past the Mirmen crossing, past
> that, on into the scrub — in one season, one cutting program, one hand. Then the Empire didn't come. The
> markers stayed. That is why the stone in front of you, standing in country the Empire has never in its life
> administered, is a genuine imperial boundary stone in perfect order: it is a monument to an intention.
>
> So the chain is longer than the Empire, and always has been. Which means the frontier cannot be "where the
> stones are." It has to be *declared* — at a named stone, in the roll.
>
> And every trader on this road knows the saying. The Empire stops about the fifth stone beyond Casra Nuvicerre.
>
> *About.* Nobody has ever needed to be more precise than that, because the stone was there and stones do not
> walk.
>
> You have just spent a night proving that the fifth stone beyond Casra Nuvicerre is standing one league further
> out than the survey put it.
>
> It does not need two stones. It never needed two.
>
> Ahead, the rain thins enough to show the valley properly: the Mirmen running brown and wide, a stone-built
> waystation on the near bank with a newer palisade thrown up around it, and men on the bank in the wet, doing
> something to a rope.

---

**PLAYER —**

> Ok, so... The *fifth* stone from Casra Nuvicerre is (supposed to be) 11 leagues out, but each stone is about
> a league from the previous? What happened to the other 6?
> And who would tamper with the stone? Who cares if the Empire stops 5 or 6 stones from Casra Nuvicerre when
> there isn't anything between the 5th and 6th stones? (or where those stones would be if untampered)
> I think I need some more clues here or something.
> Otherwise, I think we just continue to the way station.

---

**GM —** [**Second bookkeeping error caught by the player, and this one was mine.** "About the fifth stone
beyond Casra Nuvicerre" does not survive contact with ~1-league spacing over 11 leagues. Corrected out of
character in one line and replaced with an identifier that works — and is better, because it makes the
inscription's own figure load-bearing. Also gave more, per `CLAUDE.md`: "when you're unsure how much to give,
give more."]

> Straight correction, my error: I had Edward call it "about the fifth stone beyond Casra Nuvicerre," and you're
> right that the count doesn't work — the stones don't run a league apart for eleven leagues and land on five.
> Scratch the counting version. The saying goes by the figure, not the tally, and that turns out to matter:
>
> **"The Empire stops at the eleven-league stone."**
>
> That's how it's said, because that is how it's *found*. Nobody out here counts markers — they read them. A
> carter who wants to know whether he's inside walks until he finds the stone whose face says eleven leagues to
> Casra Nuvicerre, and that is the frontier, and the roll at Casra says the same thing in more words.
>
> Which means the frontier is not at a place. It is wherever the stone that says *eleven* happens to be standing.
>
> You have spent a night proving that the stone which says eleven is standing at twelve.
>
> As for who cares — you don't know. Nothing lives out there. You went past it in the dark and you'll go past the
> rest of it in the rain: grey rock, a dry watercourse, scrub that isn't grazed because there's nobody to graze it.
>
> ---
>
> You walk it down. Three leagues of switchbacked road losing height into the valley, the rain slackening to a
> mizzle that gets into everything anyway.
>
> Destrio talks, because walking downhill loosens him and because his one subject is money.
>
> "Fifth time down this road this year, and every time back up it I'm lighter." He's watching his own wheels, not
> you. "That's the part that galls. Going out I carry iron and fish sauce and he waves me through like I'm nothing,
> because I *am* nothing, going out. Coming back's when he's got his hand out. Coming back I've the odd crate of
> what the diggers sell me — lamps, buckles, a bronze thing shaped like a duck that I still can't shift — and he
> wants the Empire's half of it. On a bronze duck." He spits. "Four times. Four times I've handed over the Empire's
> half of a duck."
>
> The waystation comes up out of the murk as the road flattens.
>
> It's Auran and it's old — proper coursed masonry, a squat rectangle with a tiled roof patched in three colours,
> the sort of thing put up when the Empire meant business here. The palisade around it is new by comparison, twenty
> years at the outside, raw stakes and green withies. There's a stockade for animals, smoke from two fires, and
> washing strung under an awning that will not be drying today.
>
> Your eye goes to the footings, because it always does. The lowest course of the waystation wall is not the same
> stone as the rest of it. Bigger blocks, dressed, darker, laid in as foundation the way builders have always robbed
> out whatever was lying about. One of them, half-buried at the corner, carries the tail of an inscription running
> off into the ground.
>
> You've read that hand once already, four hours before dawn, on your knees in a hole.
>
> At the bank, six or seven men are working a heavy rope across the brown water, and the water is well up over
> whatever stepping-stones there used to be.
>
> One of them has seen the wagons and is walking up the road toward you. He isn't hurrying and he isn't armed.

---

**PLAYER —**

> Let's see what he has to say then. I can check that footing later.

---

**GM —** [chaos lowered 5 → 4 (player ended the stone-6 scene more in control); Quellus's clock ticked 2 → 3;
Otho created with a name and a want. Decided Quellus's posture from INTENTION rather than the oracle, per
`CLAUDE.md`: he is not suspicious, he is *interested*.]

> He is about forty, Tirenean by the look of him, and he is wearing a military cloak that stopped being military
> some years ago — the fittings are gone off it and it has been re-hemmed by somebody's wife. He has a hood he isn't
> using and hair plastered flat. He is picking his way along the drier edge of the road with the fixed concentration
> of a man whose boots are already wet and who is going to keep the rest of himself out of it as a matter of principle.
>
> "Mennicus." He says it without checking, so he knows the wagons. "You're a day behind."
>
> "I'm a day behind," Destrio agrees, in the sour voice he promised you.
>
> "Ford's up. Went over at second bell yesterday and it's still coming." He tips his head back toward the water, where
> the rope crew have got a line most of the way across and are arguing about it. "We'll have the raft on by dusk if the
> rain quits. Two crossings tonight if you want them, four tomorrow. There's a charge for it — that's separate, that's
> the ferry, that's not the other thing." He says this last part quickly, like a man repeating a formula he's been
> drilled on and does not want to be blamed for.
>
> "Standing's up behind the palisade, dry-ish. Fodder if you're buying. Don't let your people down to the bank after
> dark, the mud takes a leg off you."
>
> He looks past Destrio at the line of wagons, at the crew unhitching, at you. Then back at Destrio, and asks it
> plainly, the way you'd ask about a wheel:
>
> "Which of you reads?"

---

**PLAYER —**

> "That'd be me." This doesn't seem like it'd be suspicious to ask, so I won't seem suspicious to answer

---

**GM —**

> Something goes out of Otho's shoulders. He'd been told to ask and he has asked and that part of his day is done.
>
> "Good. Right." He wipes rain off his face with the flat of his hand and looks briefly, genuinely relieved. "Then
> you'll want to come up. He's asking."
>
> He says it the way a man says the cook wants you, and starts walking before he's checked whether you're following,
> which is its own kind of answer about how often anybody says no here.
>
> "He's been up since midnight with his papers out on the table. Candles going. I've not seen him do that since the year
> before last." A grunt that might be amusement or might be complaint. "So you'll be a while, I expect. Don't tell him I
> said."
>
> The palisade gate is a hurdle dragged aside on a rope. Inside is beaten mud, duckboards laid in the worst of it, the
> two fires under an awning, a stack of split wood under another. The waystation door is oak and open, and there is light
> in there — proper light, several candles' worth, in the middle of a grey afternoon.
>
> In the stockade to your left, out of the weather with the crossing's animals, there is a mule with a saddle blanket over
> the rail beside it. You have walked six days behind that mule.
>
> Nobody remarks on it.
>
> Otho is at the door, holding it, waiting on you with the patience of a man who is already as wet as he is going to get.

---

**PLAYER —**

> I go on in.

---

**GM —** [core clue delivered as pure observation, never gated: the thumb on the term clause]

> The room is better than the building deserves. Somebody has kept it: the hearth swept, the flags mopped, the Auran
> masonry pointed where it had started to shed. There is a folding campaign table in the middle of it, the real thing,
> bronze-hinged, army issue, and it is the only object in the room that has not been mended. Everything else has: the
> chair, the shutters, the bucket, the man.
>
> He is about fifty. He is clean-shaven, which nobody out here is, and he has done it recently and not well, and there is
> a cut on his jaw. His tunic has been turned. Over it he wears a soldier's belt — the plates polished to a shine you could
> read a page by, the leather oiled, the buckle sound. In this room the belt is the only thing that is not four years old
> and tired, and it is four years old and tired too; it has just been *maintained*, daily, by a man with time.
>
> There are seven candles going. Seven. In the afternoon.
>
> The table is covered in paper laid out in courses like masonry: a roll with a lead seal still on its cord, ledgers, and a
> great stack of letter-copies with their edges gone furry from handling.
>
> "Quellus Tarcalus," he says. "Limitanus." He does not offer a hand; he inclines his head, which is a formal thing, and an
> old thing, and he does it properly. "You'll want to sit before you're asked twice. Otho, the door."
>
> The door goes. Otho does not come in.
>
> "Edward Copper," he says, testing it. "Krysean. Mennicus took you on at Kavala to read the line in." Not a question, and he
> doesn't dress it up as one. "Classical Auran, is it. Not the trade hand — the *cut* hand. Formulae. Reigns."
>
> He turns the seal-roll a quarter turn on the table so it faces you, without unrolling it, and rests two fingers on it.
>
> "Then I'll ask you the thing I've been asking for three years and getting nothing but shrugs for."
>
> He leans in slightly. The candles do what candles do to a face that has been awake all night.
>
> "How many of them did you read on the way down? All of them, or only the ones the daylight fell on?"

---

**PLAYER —**

> "All of them, sir. That was the job."

---

**GM —** [Quellus makes his ask: an attestation that the bound is sound, for eight sun and free passage. He is
sincere. His guilt is one question away but he does not volunteer it here.]

> Something happens in his face that he puts away almost at once, and it is not triumph. It is closer to the look of a man who
> has been carrying something heavy and has just been told there is a cart coming.
>
> "All of them." He repeats it. "*That was the job.*"
>
> He gets up. He is not a big man and he moves stiffly on one side. He unties the cord on the sealed roll and lays it open on the
> table with the flat of both hands, the way you'd handle something you'd been shown how to handle.
>
> It is a commission. Imperial, properly drawn, the hand of a provincial chancery and not a good one but a real one. The lead seal
> is on its cord, uncracked, and it is genuine — you have seen that die a hundred times on charters, and this is that die. *Quellus
> Tarcalus, to the customs of the Mirmen crossing and the road thereto, in the name of the Emperor* — and there is a term clause,
> because there is always a term clause.
>
> His right thumb is resting on the line where the term clause gives its dates.
>
> It does not move.
>
> "Fourteen reports west in four years," he says. "Two answered. Both in the first year, both from a clerk, both telling me the
> office was moving. I have the copies. I keep everything." He touches the furry-edged stack, and then, deliberately, does not touch
> the ledgers beside it. "I have not been relieved. That's the word for it. *Unrelieved.* A man can be unrelieved for a long time
> and still be at his post, and being at your post is the whole of it."
>
> He looks up.
>
> "Here is what I want and I'll pay for it. I want a statement. Written, in your hand, in the proper form, saying who you are and
> what you read and that you are competent to read it — and saying that the eleven-league stone stands where the survey of Ulkyreus
> set it. That's all. One page. A qualified reader has walked the whole line down from Casra Nuvicerre and finds the bound in order."
>
> He says it without a flicker, because he believes every word of it.
>
> "Eight sun for the page. And Mennicus goes over tonight on the first raft with no charge on the ferry, which is mine to give and
> I'll give it."
>
> Outside, faintly, men are shouting about the rope.
>
> "Three years I've asked. Everybody who comes through this crossing can read a tally and not one of them can read a stone."
