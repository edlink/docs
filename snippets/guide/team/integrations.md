<p v-if="team.type === 'developer'">
    This page contains a list of the districts that are connected to your `Applications`. Each connection forms an `Integration`.
</p>

<p v-if="team.type === 'district'">
    This page contains a list of the `Applications` that are connected to your district. Each connection forms an `Integration`.
</p>

Clicking on any of the items on this page will show you more details about an integration. From there, you can set sharing rules, browse shared data, impersonate users, and view request logs.