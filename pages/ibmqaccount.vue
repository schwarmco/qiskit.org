<template>
  <main>
    <LegacyPresentation
      :title="title"
      image="/images/qiskit-ibmqp-logo.svg"
      :description="description"
      sources="https://github.com/Qiskit/qiskit-ibmq-provider"
      segment-action="IBM Q Account: GitHub Repository"
    />
    <LegacySection>
      <article>
        <h2>About</h2>
        <p>
          Your IBM Q Account is the doorway for accessing the full suite of
          cloud-based IBM Q quantum systems and simulators. From job submission
          and tracking to viewing detailed quantum device properties, the IBM Q
          Account connects the proven Qiskit software framework to the most
          advanced quantum computing platforms on the planet.
          <a
            class="colored-link"
            href="https://qiskit.org/documentation/install.html#access-ibm-q-systems"
            title="Link"
            rel="noopener"
            target="_blank"
            @click="$trackClickEvent({
              action: 'Link to Access IBMQ Systems'
            })"
          >
            Follow these steps
          </a>
          to set up your Qiskit environment to send jobs to IBM Q systems.
        </p>
      </article>
      <article>
        <h2>Example</h2>
        <!-- eslint-disable vue/multiline-html-element-content-newline -->
        <!-- eslint-disable vue/html-indent -->
        <SyntaxHighlight
          lang="python"
          :label="title"
        >from qiskit import IBMQ
from qiskit.providers.ibmq import least_busy

# Load local account information
provider = IBMQ.load_account()

# Get the least busy real quantum system
backend = least_busy(provider.backends(simulator=False))
print(backend, backend.status().pending_jobs)</SyntaxHighlight>
        <!-- eslint-enable vue/html-indent -->
        <!-- eslint-enable vue/multiline-html-element-content-newline -->
      </article>
    </LegacySection>
  </main>
</template>

<script lang="ts">
import { Component } from 'vue-property-decorator'
import QiskitElementPage from '~/components/qiskit/QiskitElementPage.vue'
import LegacyPresentation from '~/components/headers/LegacyPresentation.vue'
import LegacySection from '~/components/sections/LegacySection.vue'
import SoftwareStack from '~/components/qiskit/SoftwareStack.vue'
import SyntaxHighlight from '~/components/qiskit/SyntaxHighlight.vue'
import Cta from '~/components/ctas/Cta.vue'

@Component({
  layout: 'legacy',
  components: {
    Cta,
    LegacyPresentation,
    LegacySection,
    SoftwareStack,
    SyntaxHighlight
  },
  head (this: QiskitElementPage) {
    return {
      title: `${this.title} | ${this.description}`,
      link: [
        { rel: 'stylesheet', href: 'https://cdnjs.cloudflare.com/ajax/libs/highlight.js/9.9.0/styles/atom-one-dark.min.css' }
      ]
    }
  }
})
export default class extends QiskitElementPage {
  title = 'IBM Q Account'
  description = 'Access to world-leading quantum systems and simulators.'
  routeName = 'ibm-q-account'
}
</script>

<style lang="scss">
@import '~/assets/scss/legacy-elements.scss';
</style>

<style lang="scss" scoped>
.legacy-presentation {
  --legacy-presentation-color: rgb(201, 222, 255);
  --legacy-presentation-text-color: black;
}

.legacy-section {
  background-color: white;
}
</style>
