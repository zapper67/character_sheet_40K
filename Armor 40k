var rollResultForArmor40k = function (token, armure, dommagearmure, pvarmure, emp) {
	var temparmure = parseInt(armure);
	var tempdommagearmure = parseInt(dommagearmure);
	var temppvarmure = parseInt(pvarmure);
	var output ='<span style="color:blue">', token;
	var rocky = (temparmure *3);
	var test = ' pourquoi ...';

        switch (emp) {
	case 'TÊTE':
		test = ' sur la tête !';
		break;
	case 'BRAS DROIT':
		test = ' sur le bras droite !';
		break;
	case 'TORSE':
		test = ' sur le torse !';
		break;
	case 'BRAS GAUCHE':
		test = ' sur le bras gauche !';
		break;
	case 'JAMBE DROITE':
		test = ' sur la jambe droite !';
		break
	case 'JAMBE GAUCHE':
		test = ' sur la jambe gauche !';
		break;
	}

        while ((tempdommagearmure >= rocky) && (rocky != 0)) {
            temparmure = (temparmure-1);
            tempdommagearmure = (tempdommagearmure - rocky);
            rocky = (temparmure *3);
        } 

    output +=token+' à encore : '+ temparmure + ' d armure '+test;
	//Return output
	return output ;
};


/** Interpret the chat commands. **/
on('chat:message', function (msg) {
	'use strict';
	var cmdName = '!armor40k ';


	if (msg.type === 'api' && msg.content.indexOf(cmdName) !== -1) {
		var paramArray = msg.content.slice(cmdName.length).split(',');
		if (paramArray.length !== 5) {
			sendChat(msg.who, '/w ' + msg.who + ' must specify seven comma-separated ' +
				'parameters for the !armor40k command.');
		}
		else {
			var result = rollResultForArmor40k(paramArray[0].trim(),
				paramArray[1].trim(),
				paramArray[2].trim(),
				paramArray[3].trim(),
				paramArray[4].trim());
			sendChat(msg.who, result);
		}
	}
});