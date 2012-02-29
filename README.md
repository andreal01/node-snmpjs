snmpjs provides a toolkit for SNMP agents and managemet application in Node.js.

## Usage

For full docs, see <http://wesolows.github.com/node-snmpjs/>.

	var snmp = require('./lib/index.js');
	var logger = require('bunyan');

	var log = new Logger({
		name: 'snmpd',
		level: 'info'
	});

	var agent = snmp.createAgent({
		log: log
	});

	agent.mib('.1.3.6.1.2.1.1.5', function (arg) {
		var nodename = os.hostname();
		var val = { type: 'String', value: nodename };

		snmp.util.readOnlyScalar(arg, val);
	});

	agent.bind('udp4', 161);

Try hitting that with your favourite SNMP get utility, such as:

	$ snmpget -v 2c -c any localhost .1.3.6.1.2.1.1.5

## Installation

	$ npm install snmpjs

## License

MIT.

## Bugs

See <https://github.com/wesolows/node-snmpjs/issues>.
