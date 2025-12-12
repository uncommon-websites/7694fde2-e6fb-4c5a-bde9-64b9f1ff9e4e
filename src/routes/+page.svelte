<script>
  import Header from '$lib/components/Header.svelte';
  import Hero from '$lib/components/Hero.svelte';
  import StatsGrid from '$lib/components/StatsGrid.svelte';
  import FeatureSection from '$lib/components/FeatureSection.svelte';
  import IntegrationSection from '$lib/components/IntegrationSection.svelte';
  import EngagementSection from '$lib/components/EngagementSection.svelte';
  import ComparisonTable from '$lib/components/ComparisonTable.svelte';
  import StepsSection from '$lib/components/StepsSection.svelte';
  import PricingSection from '$lib/components/PricingSection.svelte';
  import TeamSection from '$lib/components/TeamSection.svelte';
  import CTASection from '$lib/components/CTASection.svelte';
  import FAQSection from '$lib/components/FAQSection.svelte';
  import Footer from '$lib/components/Footer.svelte';
  
  import MockupFeedback from '$lib/components/MockupFeedback.svelte';
  import MockupRoadmap from '$lib/components/MockupRoadmap.svelte';
  import MockupChangelog from '$lib/components/MockupChangelog.svelte';

  const visualBuilderFeatures = [
    {
      title: "Drag-and-drop interface",
      description: "Build complex workflows visually without writing code",
      icon: `<svg class="w-6 h-6" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M7 16V4m0 0L3 8m4-4l4 4m6 0v12m0 0l4-4m-4 4l-4-4"/></svg>`,
      iconColor: "text-primary-600",
      iconBg: "bg-primary-50"
    },
    {
      title: "Conditional logic",
      description: "Create smart workflows with if/then conditions and branches",
      icon: `<svg class="w-6 h-6" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 16l2.879-2.879m0 0a3 3 0 104.243-4.242 3 3 0 00-4.243 4.242zM21 12a9 9 0 11-18 0 9 9 0 0118 0z"/></svg>`,
      iconColor: "text-purple-500",
      iconBg: "bg-purple-50"
    },
    {
      title: "Real-time testing",
      description: "Test workflows instantly with live data preview",
      icon: `<svg class="w-6 h-6" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z"/></svg>`,
      iconColor: "text-blue-500",
      iconBg: "bg-blue-50"
    },
    {
      title: "Version control",
      description: "Track changes, rollback easily, and collaborate safely",
      icon: `<svg class="w-6 h-6" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z"/></svg>`,
      iconColor: "text-green-500",
      iconBg: "bg-green-50"
    },
    {
      title: "Error handling",
      description: "Built-in retry logic and failure notifications",
      icon: `<svg class="w-6 h-6" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 9v2m0 4h.01m-6.938 4h13.856c1.54 0 2.502-1.667 1.732-3L13.732 4c-.77-1.333-2.694-1.333-3.464 0L3.34 16c-.77 1.333.192 3 1.732 3z"/></svg>`,
      iconColor: "text-orange-500",
      iconBg: "bg-orange-50"
    },
    {
      title: "Custom variables",
      description: "Store and reuse data across workflow steps",
      icon: `<svg class="w-6 h-6" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 7v10c0 2.21 3.582 4 8 4s8-1.79 8-4V7M4 7c0 2.21 3.582 4 8 4s8-1.79 8-4M4 7c0-2.21 3.582-4 8-4s8 1.79 8 4"/></svg>`,
      iconColor: "text-indigo-500",
      iconBg: "bg-indigo-50"
    },
    {
      title: "Scheduled triggers",
      description: "Run workflows on a schedule or based on events",
      icon: `<svg class="w-6 h-6" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z"/></svg>`,
      iconColor: "text-teal-500",
      iconBg: "bg-teal-50"
    },
    {
      title: "Monitoring dashboard",
      description: "Track performance, errors, and execution history",
      icon: `<svg class="w-6 h-6" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 19v-6a2 2 0 00-2-2H5a2 2 0 00-2 2v6a2 2 0 002 2h2a2 2 0 002-2zm0 0V9a2 2 0 012-2h2a2 2 0 012 2v10m-6 0a2 2 0 002 2h2a2 2 0 002-2m0 0V5a2 2 0 012-2h2a2 2 0 012 2v14a2 2 0 01-2 2h-2a2 2 0 01-2-2z"/></svg>`,
      iconColor: "text-pink-500",
      iconBg: "bg-pink-50"
    }
  ];

  const integrationFeatures = [
    {
      title: "Stripe payments",
      description: "Process payments, handle webhooks, manage subscriptions",
      icon: `<svg class="w-6 h-6" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 10h18M7 15h1m4 0h1m-7 4h12a3 3 0 003-3V8a3 3 0 00-3-3H6a3 3 0 00-3 3v8a3 3 0 003 3z"/></svg>`,
      iconColor: "text-purple-500",
      iconBg: "bg-purple-50"
    },
    {
      title: "Webhook automation",
      description: "Trigger workflows from any webhook event",
      icon: `<svg class="w-6 h-6" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z"/></svg>`,
      iconColor: "text-blue-500",
      iconBg: "bg-blue-50"
    },
    {
      title: "Email & SMS",
      description: "Send notifications via SendGrid, Twilio, and more",
      icon: `<svg class="w-6 h-6" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"/></svg>`,
      iconColor: "text-green-500",
      iconBg: "bg-green-50"
    },
    {
      title: "Database connectors",
      description: "Connect to PostgreSQL, MongoDB, MySQL, and more",
      icon: `<svg class="w-6 h-6" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 7v10c0 2.21 3.582 4 8 4s8-1.79 8-4V7M4 7c0 2.21 3.582 4 8 4s8-1.79 8-4M4 7c0-2.21 3.582-4 8-4s8 1.79 8 4"/></svg>`,
      iconColor: "text-orange-500",
      iconBg: "bg-orange-50"
    }
  ];

  const aiModelFeatures = [
    {
      title: "One-click deployment",
      description: "Deploy ML models to production with a single click",
      icon: `<svg class="w-6 h-6" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z"/></svg>`,
      iconColor: "text-green-500",
      iconBg: "bg-green-50"
    },
    {
      title: "Auto-scaling",
      description: "Automatically scale based on demand and usage patterns",
      icon: `<svg class="w-6 h-6" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 7h8m0 0v8m0-8l-8 8-4-4-6 6"/></svg>`,
      iconColor: "text-blue-500",
      iconBg: "bg-blue-50"
    },
    {
      title: "Performance monitoring",
      description: "Track latency, throughput, and model accuracy in real-time",
      icon: `<svg class="w-6 h-6" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 19v-6a2 2 0 00-2-2H5a2 2 0 00-2 2v6a2 2 0 002 2h2a2 2 0 002-2zm0 0V9a2 2 0 012-2h2a2 2 0 012 2v10m-6 0a2 2 0 002 2h2a2 2 0 002-2m0 0V5a2 2 0 012-2h2a2 2 0 012 2v14a2 2 0 01-2 2h-2a2 2 0 01-2-2z"/></svg>`,
      iconColor: "text-orange-500",
      iconBg: "bg-orange-50"
    },
    {
      title: "Version management",
      description: "Deploy multiple versions and A/B test models easily",
      icon: `<svg class="w-6 h-6" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M7 16V4m0 0L3 8m4-4l4 4m6 0v12m0 0l4-4m-4 4l-4-4"/></svg>`,
      iconColor: "text-pink-500",
      iconBg: "bg-pink-50"
    }
  ];
</script>

<Header />

<main>
  <Hero />
  <StatsGrid />
  
  <div id="product">
    <FeatureSection 
      tag="Visual Workflow Builder" 
      tagColor="text-primary-600"
      headline="Build complex workflows with drag-and-drop simplicity"
      description="Transform your ideas into powerful automations without writing a single line of code. Our visual logic builder makes it easy to create sophisticated workflows with conditional logic, error handling, and real-time testing—all in an intuitive interface."
      features={visualBuilderFeatures}
    >
      <div slot="image">
        <MockupFeedback />
      </div>
    </FeatureSection>

    <FeatureSection 
      tag="Pre-Built Integrations" 
      tagColor="text-purple-500"
      headline="Connect to your favorite tools in seconds"
      description="Stop worrying about API documentation and webhook configurations. Our pre-built integrations for Stripe, SendGrid, Twilio, and major databases work out of the box. Just authenticate and start automating."
      features={integrationFeatures}
      quote="We built the integrations that indie hackers and SaaS founders actually need. No enterprise bloat, just the essentials that help you ship faster."
    >
      <div slot="image">
        <MockupRoadmap />
      </div>
    </FeatureSection>

    <FeatureSection 
      tag="AI Model Deployment" 
      tagColor="text-green-500"
      headline="Deploy and scale ML models without DevOps headaches"
      description="From prototype to production in one click. Macadamia handles the infrastructure, auto-scaling, monitoring, and optimization so you can focus on building great AI products. Scale to 100K models effortlessly."
      features={aiModelFeatures}
    >
      <div slot="image">
        <MockupChangelog />
      </div>
    </FeatureSection>
  </div>

  <IntegrationSection />
  <EngagementSection />
  <ComparisonTable />
  <StepsSection />
  <PricingSection />
  <TeamSection />
  <CTASection />
  <FAQSection />
</main>

<Footer />

