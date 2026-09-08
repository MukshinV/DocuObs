for ( .@quest_id = 1005; .@quest_id <= 1008; .@quest_id++ ) {
	if (isbegin_quest(.@quest_id) == 1)
		completequest .@quest_id;
}

mes "Не хочешь учиться, но хочешь знать магию?";
if (Sex == SEX_MALE)
	mes "For a cutie like you, I'd be happy to explain the requirements!";
else
	mes "I'd be happy to explain the requirements for a pretty girl like you!";

if (countitem(1071) == 0 && countitem(1085) == 0 && countitem(1086) == 0 && countitem(1087) == 0 && countitem(1090) == 0) {
	mes "Hey, where's the Solution";
	mes "I asked for...? I can't check it if you don't show it to me, right?";
	close;
}