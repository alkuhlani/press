<template>
	<span
		class="inline-block rounded-md px-3 py-1 text-xs font-medium"
		:class="classes"
	>
		<slot>{{ status }}</slot>
	</span>
</template>
<script>
export default {
	name: 'Badge',
	props: ['color', 'status', 'clickable'],
	computed: {
		classes() {
			let color = this.color;
			if (!color && this.status) {
				color = {
					Pending: 'yellow',
					Running: 'yellow',
					Success: 'green',
					Failure: 'red',
					Active: 'green',
					Broken: 'red',
					Updating: 'blue',
					Installing: 'yellow',
					Rejected: 'red',
					'Update Available': 'blue',
					Enabled: 'blue',
					'Awaiting Approval': 'yellow',
					'Awaiting Deploy': 'yellow',
					Published: 'green',
					Approved: 'green',
					Deployed: 'green',
					Expired: 'red',
					Paid: 'green'
				}[this.status];
			}
			let cssClasses = {
				gray: 'text-gray-700 bg-gray-50',
				green: 'text-green-700 bg-green-50',
				red: 'text-red-700 bg-red-50',
				yellow: 'text-yellow-700 bg-yellow-50',
				blue: 'text-blue-700 bg-blue-50'
			}[color || 'gray'];
			cssClasses += ' ';
			cssClasses += this.clickable ? 'cursor-pointer' : 'cursor-default';

			return cssClasses;
		}
	}
};
</script>
