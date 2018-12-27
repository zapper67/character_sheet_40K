var rollResultForSkill40k = function (token, attribute, skillBn1, skillBn2, skillBn3, skillBn4, modifier) {
	var roll = randomInteger(100);
	var skillBonus = parseInt(skillBn1) + parseInt(skillBn2) + parseInt(skillBn3) + parseInt(skillBn4) - 20;
	var modTarget = parseInt(attribute) + skillBonus + parseInt(modifier);
	var output1 = token,
		output2, degOfSuc;


	//Create output which includes skill level wording
	switch (skillBonus) {
	case 0:
		output1 += ' is known (0)';
		break;
	case 10:
		output1 += ' is trained (+10)';
		break;
	case 20:
		output1 += ' is experienced (+20)';
		break;
	case 30:
		output1 += ' is veteran (+30)';
		break;
	default:
		output1 += ' is untrained (-20)';
	}
	output1 += ' granting a modified target of <B>' + modTarget + '</B>. They ' +
		'rolled a <B>' + roll + '</B>.';


	//Form output message based on result
	if (roll === 1) {
		output2 = '<span style="color:green">' + token + ' rolled a 1 and automatically succeeds by <B>1 degree</B>.</span>';
	}
	else if (roll === 100) {
		output2 = '<span style="color:red">' + token + ' rolled a 100 and automatically fails by <B>1 degree</B>.</span>';
	}
	else if (roll <= modTarget) {
		degOfSuc = (Math.floor(modTarget / 10) - Math.floor(roll / 10)) + 1;
		output2 = '<span style="color:green">' + token + ' succeeds by <B>' + degOfSuc + ' degree(s)</B>.</span>';
	}
	else {
		degOfSuc = (Math.floor(roll / 10) - Math.floor(modTarget / 10)) + 1;
		output2 = '<span style="color:red">' + token + ' fails by <B>' + degOfSuc + ' degree(s)</B></span>.';
	}


	//Return output
	return output1 + '<br><br>' + output2;
};


/** Interpret the chat commands. **/
on('chat:message', function (msg) {
	'use strict';
	var cmdName = '!skill40k ';


	if (msg.type === 'api' && msg.content.indexOf(cmdName) !== -1) {
		var paramArray = msg.content.slice(cmdName.length).split(',');
		if (paramArray.length !== 7 )   {
			sendChat(msg.who, '/w ' + msg.who + ' must specify seven comma-separated ' +
				'parameters for the !skill40k command.');
		}
		else {
			var result = rollResultForSkill40k(paramArray[0].trim(),
				paramArray[1].trim(),
				paramArray[2].trim(),
				paramArray[3].trim(),
				paramArray[4].trim(),
				paramArray[5].trim(),
				paramArray[6].trim());
			sendChat(msg.who, result);
		}
	}
});