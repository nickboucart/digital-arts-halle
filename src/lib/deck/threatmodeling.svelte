<script lang="ts">
	import Slide from './slide.svelte'
	import Code from './code.svelte'
	import Markdown from './markdown.svelte'
	import Notes from './notes.svelte'
</script>

<Slide>
	<h1>Threat Modelling Workshop</h1>
	<h2>Interactive walkthrough</h2>
</Slide>

<Slide>
	<h1>How this work?</h1>
	<ul>
		<li>Scroll to the right to progress through the workshop</li>
		<li>Sometimes, you'll see an arrow pointing downwards. That are examples to support that step</li>
	</ul>
</Slide>


<Slide animate>
	<h1>What to expect?</h1>
	<p>This interactive slide deck will serve as a guide when building a threat model for your own application.<br/>Through questions and examples, you'll quickly get your first TM going.</p>
	<p>Whenever there's an arrow-down symbol in the right handside corner, you'll find examples</p>

</Slide>

<Slide animate>
	<Slide>
	<h1>Our examples</h1>
	<p>We provided 2 examples to follow along: An HR SaaS application and an IoT application. Those are ficticious examples. </p>
	<p>Scroll down to get a description of both apps</p>
	</Slide>
	<Slide>
		<h1>Example Apps</h1>
		<ul>
			<li><a href="#/saas-intro">HR SaaS Application</a></li>
			<li><a href="#/iot-intro">Iot Applicaton</a></li>
		</ul>
	</Slide>
	<Slide id="saas-intro">
		<p>The HR SaaS application is an app to manage soft HR processes. These include organigrams, 360 reviews, employee data such as name, address, social security numbers etc.
			 Employer contracts are managed with the app as well.<br/> Users interact with the SaaS through a single page webapp.<br/>
			HR is typically the power user of the application, while non-HR employees typically use the app a few times per year during reviews or for an occasional update of their personal data.</p>
	</Slide>
	<Slide id="iot-intro">
		<p></p>
	</Slide>

</Slide>

<Slide>
	Let's start!
</Slide>

<Slide>
<h1>Context of your application</h1>
<p>First step in TM is to understand the role of your applicaton in it's broader context. We'll make a schematic drawing of that context, using the <a href="https://c4model.com/">C4 Model</a></p>
</Slide>	

<Slide>
	<Slide>
	<h1>The context of your application</h1>
	<ul>
		<li>What types of users are accessing your system, with what clients?</li>
		<li>What are the most important systems your system is interacting with?</li>
		<li>What are the different types of data that are flowing throught your system?</li>
		<ul>
			<li>Authentication and authorization data</li>
			<li>Application data</li>
			<li>Telemetry data</li>
			<li>...</li>
		</ul>

	</ul>
</Slide>
	<Slide>
		<h1>Examples</h1>
		<ul>
			<li><a href="#/saas-context">HR SaaS Application</a></li>
			<li><a href="#/iot-context">Iot Applicaton</a></li>
		</ul>
	</Slide>
	<Slide id="saas-context">
		<Slide>
			<h1>HR SaaS application</h1>
		<p>The example HR SaaS application is an application to man </p>
		</Slide>
	</Slide>
	<Slide id="iot-context">Todo, description of iot app context</Slide>
</Slide>