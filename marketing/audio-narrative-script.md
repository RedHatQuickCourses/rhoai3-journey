# Audio Narrative Script: The RHOAI 3.x Journey
## A Conversation About Industrializing AI

**Format:** Podcast-style conversation  
**Duration:** ~8-10 minutes  
**Speakers:** Alex (curious co-worker) and Jordan (narrator/journey creator)  

---

### COLD OPEN

**JORDAN:**  
You know that feeling when you find a rogue LLM API key in production code... and the bill is $43,000?

**ALEX:**  
*(laughs nervously)* Please tell me that didn't actually happen.

**JORDAN:**  
It did. To a company I won't name. Engineering team was "experimenting" with Claude API. One intern hardcoded the key. One viral internal chatbot. One very expensive Monday morning.

**ALEX:**  
Ouch.

**JORDAN:**  
Yeah. That's what we call "Shadow AI"—and it's happening right now in every enterprise. Which is why we built the RHOAI 3.x Journey.

---

### INTRO

**ALEX:**  
Okay, I'm intrigued. You mentioned this in the team meeting last week—something about going from "token consumer to token producer"? What does that even mean?

**JORDAN:**  
Great question. So right now, most organizations are in this weird AI adolescence. Teams are using ChatGPT, Claude, OpenAI APIs... burning through budget with no governance, no cost controls, sending proprietary data to external providers. It's like running a factory by ordering parts from Amazon every single day instead of, you know, actually manufacturing anything yourself.

**ALEX:**  
*(laughs)* That's... actually a perfect analogy. So the journey is about building your own factory?

**JORDAN:**  
Exactly. It's about flipping the script—from consuming AI tokens from external vendors to producing them on your own infrastructure. On-premise. Governed. Predictable costs. Full data sovereignty.

**ALEX:**  
And this is using Red Hat OpenShift AI 3.x?

**JORDAN:**  
Yep. RHOAI 3.x gives you the platform, and the journey gives you the roadmap. Think of it as the difference between getting a pile of lumber and a blueprint versus getting a pile of lumber and a YouTube video titled "How to build a house (probably)."

**ALEX:**  
*(laughs)* Okay, I'm sold on the metaphor. But what's the actual problem you're solving? Like, real-world pain points?

---

### THE PROBLEM

**JORDAN:**  
Alright, let me paint the picture. You're a platform engineering team at a mid-size enterprise. Maybe 5,000 employees. You've got:

- Data science teams burning $50K to $200K per year *per team* on external API calls with zero cost controls  
- GPU nodes sitting at 20-30% utilization because teams over-reserve resources and then hoard them like dragons guarding gold  
- Security team discovering unauthorized AI services during compliance audits—Slack bots, Excel macros with API keys, you name it  
- No model versioning, no governance, no idea what's actually running in production  

**ALEX:**  
Okay yeah, that's... that's terrifying and also very familiar.

**JORDAN:**  
Right? And here's the kicker—this isn't hypothetical. We're seeing this pattern everywhere. The AI revolution is real, but most companies are revolutionizing themselves straight into technical debt and compliance nightmares.

**ALEX:**  
So what changes? What does the "after" look like?

**JORDAN:**  
After the journey? Completely different world. Self-service model deployment through a governed catalog—teams can provision models in *minutes* instead of submitting tickets and waiting weeks. GPU utilization jumps from 20% to 70-85% through time-slicing and fair-share queuing. External API spend drops 70-90%. Complete audit trail for every model—version control, tracking, governance. And your platform team? They're not firefighting anymore. They're running an internal Model-as-a-Service operation.

**ALEX:**  
Wait, those numbers are real? 3-to-5x GPU utilization improvement?

**JORDAN:**  
Real numbers from real deployments. And honestly, 5x is conservative if you're starting from a really inefficient baseline.

---

### THE APPROACH

**ALEX:**  
Okay, so I'm convinced this is worth doing. But here's my concern—I've seen these "transformation initiatives" before. They take 18 months, involve 47 consultants, and produce a 300-page document nobody reads. How is this different?

**JORDAN:**  
*(laughs)* Yeah, fair. So here's where the journey approach is fundamentally different. We call it the "cookbook method" versus the "dictionary method."

**ALEX:**  
Explain.

**JORDAN:**  
Traditional training says: read all the documentation, become an expert, *then* deploy. That's the dictionary—you learn every word before you write a sentence. The journey flips it: operationalize first, understand second, optimize third.

**ALEX:**  
So you're deploying before you fully understand it?

**JORDAN:**  
You're deploying *proven patterns* before you reinvent the wheel. Every phase gives you automation scripts that get features running in hours. Then, while it's running, you learn the business value. Then you optimize for your specific needs.

**ALEX:**  
Huh. That actually makes sense. Learn by doing.

**JORDAN:**  
Exactly. And the time savings are massive. If you learned each feature from scratch—reading docs, trial-and-error, troubleshooting weird edge cases—you're looking at 120 to 200 hours minimum.

**ALEX:**  
Yikes.

**JORDAN:**  
With the journey? 30 to 50 hours total. From greenfield cluster to production AI platform.

**ALEX:**  
That's like a 70% time reduction.

**JORDAN:**  
Exactly 70 to 75 percent, yeah. And that's not marketing fluff—that's based on actual practitioner feedback from people who've done both paths.

---

### THE JOURNEY

**ALEX:**  
Alright, walk me through it. What are the phases?

**JORDAN:**  
Four main phases, plus a foundation phase. Phase 0 is the operator ecosystem—basically installing all the infrastructure operators. NVIDIA GPU operator, Kueue for job queuing, cert-manager, the works. Takes about 2 to 4 hours.

**ALEX:**  
Okay, that's the plumbing.

**JORDAN:**  
Right. Then Phase 1 is "Assembling the Factory"—and this is where it gets strategic. You're building your model supply chain and governance layer. Model registry backed by a real database, model catalog so teams aren't just downloading random stuff from HuggingFace, hardware profiles that abstract away all the Kubernetes complexity, and GPU-as-a-Service configurations.

**ALEX:**  
Wait, GPU-as-a-Service? Like, multiple workloads sharing GPUs?

**JORDAN:**  
Exactly. Time-slicing, multi-instance GPU, fair-share queuing. That's how you go from 20% utilization to 70%. This phase takes 8 to 12 hours, and by the end you've basically eliminated Shadow AI because everything goes through a governed pipeline.

**ALEX:**  
Okay, that's huge. What's Phase 2?

**JORDAN:**  
Phase 2 is the "Token Production Engine"—this is where you actually start serving models. KServe for the serving architecture, vLLM for high-throughput inference, and you learn all the VRAM sizing math so you don't, you know, run out of memory mid-inference like a rookie.

**ALEX:**  
*(laughs)* Sounds like you've been there.

**JORDAN:**  
Oh, we've *all* been there. This phase also covers model compression—when it makes sense to use lower precision models to save resources. Takes 6 to 10 hours.

**ALEX:**  
And Phase 3?

**JORDAN:**  
Phase 3 is "Scaling the Utility." Distributed inference with llm-d for massive workloads, Model-as-a-Service APIs with gateway and multi-tenancy, observability with Prometheus and Grafana. This is where you stop being a platform team and start being an internal AI product team. Another 6 to 10 hours.

**ALEX:**  
So we're at... what, 30 to 40 hours total?

**JORDAN:**  
Yeah, and there's a Phase 4 for governance and trust frameworks—TrustyAI, guardrails, the stuff you need for compliance and safe AI. But honestly, phases 0 through 3 get you to production. Phase 4 is when you're ready for autonomous agents and really locked-down environments.

---

### THE REAL TALK

**ALEX:**  
Okay, real talk though. This sounds great in theory. What's the catch? What are the hard parts?

**JORDAN:**  
*(pause)* Good question. So first, this isn't magic. You still need actual GPU hardware. If you're trying to do this on CPU nodes with no acceleration, you're gonna have a bad time.

**ALEX:**  
Fair.

**JORDAN:**  
Second, this is opinionated. We made architectural decisions for you—like using vLLM instead of other inference engines, using KServe, using Kueue for scheduling. If you want to debate every choice and build a custom stack, this isn't for you. This is for teams that want proven patterns.

**ALEX:**  
I actually see that as a feature, not a bug.

**JORDAN:**  
Yeah, most people do. But you'll definitely get that one architect who wants to bikeshed every decision. Just... be ready for that conversation.

**ALEX:**  
*(laughs)* Oh, I know that person. They're in every organization.

**JORDAN:**  
Third hard part: change management. You're not just deploying technology—you're changing how teams consume AI. Some teams will love it. Some will resist because they liked their chaotic freedom.

**ALEX:**  
Yeah, that's real. How do you handle that?

**JORDAN:**  
Show them the GPU utilization graphs. Show them the cost savings. Show them the self-service catalog where they can deploy a model in 5 minutes instead of waiting 3 weeks for a ticket. Wins speak louder than mandates.

---

### THE HUMOR

**ALEX:**  
Okay, I have to ask—you keep calling it a "token production factory." Is that just marketing or are we really treating AI like... industrial manufacturing?

**JORDAN:**  
*(laughs)* I mean, yes? Think about it. You've got raw materials—your models and data. You've got machinery—your GPUs. You've got quality control—your validation services. You've got distribution—your MaaS APIs. It's literally a factory.

**ALEX:**  
That's either genius or slightly dystopian.

**JORDAN:**  
Why not both? *(laughs)* But seriously, the metaphor works because it forces you to think about efficiency, utilization, governance, quality. You wouldn't run a real factory where anyone can walk in and grab machinery whenever they want with no tracking.

**ALEX:**  
True. Although... I've worked at startups where that's basically how the AWS account worked.

**JORDAN:**  
*(laughs)* Okay, yeah, fair point. And that's exactly the problem we're solving—but for AI.

---

### THE CALL TO ACTION

**ALEX:**  
Alright, I'm convinced. This sounds like something we should pilot. Where do I start?

**JORDAN:**  
Two paths. If you want to just learn and deploy on your own infrastructure, the whole journey is public. The course materials, the scripts, everything. It's at the RHOAI 3.x Journey site.

**ALEX:**  
Okay, that's path one. What's path two?

**JORDAN:**  
Path two is for people who want to contribute—either to the journey itself or to create their own QuickCourses using our approach. We built this whole thing with a learner guide at `/rhoai3-journey-learner-guide.html` that walks you through the full contribution workflow.

**ALEX:**  
Wait, you're open-sourcing the approach?

**JORDAN:**  
Absolutely. The whole thing is built with Claude Code skills, Antora documentation, AsciiDoc. If you want to create a new course on, say, "Phase 5: AI Observability at Scale," the learner guide shows you exactly how to do it—from using the QuickCourse template to integrating it into the journey.

**ALEX:**  
That's actually really cool. So someone could add to this?

**JORDAN:**  
Yeah, and we *want* them to. This journey covers RHOAI 3.x features, but there's always new stuff—new operators, new patterns, new optimizations. If you've figured out something brilliant, contribute it. Make it part of the journey.

**ALEX:**  
Okay, I love that. Community-driven but with governance.

**JORDAN:**  
Exactly. It's like... *(pauses)* okay, here's the meta-level thing. We built this journey using the same principles we're teaching. Modular, reusable, governed, collaborative. The journey is practicing what it preaches.

**ALEX:**  
That's actually perfect. Self-referential consistency.

**JORDAN:**  
*(laughs)* Yeah, we're very proud of our recursive architecture.

---

### THE CLOSE

**JORDAN:**  
So look, here's the bottom line. Shadow AI is happening in your organization right now. The question isn't whether you'll industrialize your AI infrastructure—it's whether you do it strategically with a roadmap, or reactively after something breaks expensively.

**ALEX:**  
Like a $43,000 API bill.

**JORDAN:**  
*(laughs)* Exactly like a $43,000 API bill. The journey gives you the roadmap. You bring the execution. And if you learn something along the way, contribute it back so the next team doesn't have to reinvent the wheel.

**ALEX:**  
I'm in. Sending this to my team right now.

**JORDAN:**  
Awesome. And hey, when you deploy your first model through the governed catalog and your GPU utilization jumps to 80%, send me a screenshot. I collect those.

**ALEX:**  
*(laughs)* You collect GPU utilization screenshots?

**JORDAN:**  
It's a niche hobby. Don't judge me.

**ALEX:**  
No judgment. Just... maybe get out more.

**JORDAN:**  
Says the person about to spend 40 hours building an AI platform.

**ALEX:**  
Fair point.

---

### OUTRO

**JORDAN:**  
Alright, that's the RHOAI 3.x Journey. From Shadow AI to strategic asset. From token consumer to token producer. From 120 hours of guesswork to 40 hours of proven patterns.

Check out the journey at the RHOAI 3.x site. Read the condensed overview. Dive into the learner guide. Deploy something. Break something. Fix it. Learn from it. And then—here's the important part—contribute what you learned so the next person doesn't have to struggle with the same problem.

That's how we turn AI infrastructure from a cost center into a competitive advantage.

That's the journey.

Now go build something.

---

**[END]**

---

## Production Notes

**Tone:** Conversational, professional but approachable, occasional humor without being unprofessional

**Pacing:** Natural pauses for comprehension, not rushed

**Alex character:** Intelligent skeptic who asks good questions, represents the audience

**Jordan character:** Knowledgeable but not condescending, uses metaphors and humor, speaks from experience

**Call to action:** Clear pointers to both consumption (using the journey) and contribution (learner guide)

**Key beats to emphasize:**
- The real pain of Shadow AI (makes it relatable)
- The cookbook vs. dictionary approach (differentiator)
- Time savings (70% reduction = 30-50 hrs vs. 120-200 hrs)
- Real outcomes (GPU utilization, cost reduction)
- Contribution opportunity (learner guide reference)

**Runtime:** 8-10 minutes at conversational pace with natural pauses

**Recording tips:** 
- Have two voice actors if possible (makes conversation feel real)
- Allow natural overlaps and interruptions for authenticity
- Don't over-produce—keep it feeling like a real conversation
- Background music: subtle, professional, not distracting
