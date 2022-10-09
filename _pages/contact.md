---
layout: page
title: Contact
permalink: /contact/
---

Whether you want to discuss a project, ask a question, or just say hi, feel free to contact me!

<div id="formkeep-embed" data-formkeep-url="https://formkeep.com/p/3c73cadaaeef1bfc4ac746642708b2d5?embedded=1"></div>

<script type="text/javascript" src="https://pym.nprapps.org/pym.v1.min.js"></script>
<script type="text/javascript" src="https://formkeep-production-herokuapp-com.global.ssl.fastly.net/formkeep-embed.js"></script>

<!-- Get notified when the form is submitted, add your own code below: -->
<script>
const formkeepEmbed = document.querySelector('#formkeep-embed')

formkeepEmbed.addEventListener('formkeep-embed:submitting', _event => {
  console.log('Submitting form...')
})

formkeepEmbed.addEventListener('formkeep-embed:submitted', _event => {
  console.log('Submitted form...')
})
</script>