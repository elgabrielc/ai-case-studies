# AI Case Studies

A curated index of AI case studies by Gabriel Casalduc — built with (a d resulting from) Claude Code, Codex, Comet, Grok, Gemini, etc.

These are actual occurrences and functioning/attempted workflows, not demos or thought experiments.

---

## Case Studies

### 1. Browser-Native Research and Outreach — Comet
**[View HTML page for best explanation](https://elgabrielc.github.io/ai-case-studies/)**

**[View Gist for shorter text-only version](https://gist.github.com/elgabrielc/4790a52924ddde74830f932699db6f69)**

Started from a live Gmail thread with the Perplexity Fund team. Comet summarized the thread, identified the full fund team, and surfaced verified personal emails for each member — without leaving the browser tab. Documents how browser-native AI compresses page understanding, stakeholder mapping, and contact discovery into one continuous session.

---

### 2. Product Marketing Case Study
**[View Project](https://elgabrielc.github.io/product-marketing-case-study/)** · [Repo](https://github.com/elgabrielc/product-marketing-case-study)

A product marketing case study built and deployed as a live web page via GitHub Pages.

---

### 3. PDF Visual Skill — Claude Code
**[View Repo](https://github.com/elgabrielc/pdf-visual-skill)**

A Claude Code skill that automatically reads PDFs visually when text parsing fails. Built to solve a real gap in how LLMs handle complex PDF documents — falls back to visual rendering when text extraction is insufficient.

---

## About

Gabriel Casalduc is the solo founder at [DIVERGENT.health](https://divergent.health) and [myRadOne.com](https://myradone.com). Mechanical engineer via Stanford,turned independent SWE via the inexorable progress of information technology. These case studies illustrate deep, day-to-day use of AI tools in a real product and business context. Also examples of failure modes and complex system orchestration at the bleeding edge of (publicly accessible) AI capabilities. 


## running list for easy addition on the go


https://photos.app.goo.gl/k2CrPLC6eFUyAk6r5

<img width="1936" height="1256" alt="image" src="https://github.com/user-attachments/assets/5a8dc32a-b9a0-4105-8499-019594952c3f" />

<img width="1766" height="1172" alt="image" src="https://github.com/user-attachments/assets/f892ea29-840e-406a-b634-250e79756582" />

aug 18

<img width="1748" height="1756" alt="image" src="https://github.com/user-attachments/assets/c5d429dd-753b-476c-b32d-71d63cc70be5" />

"
read the project description


Viewed a file, ran a command, searched memory · 1 note
Viewed a file, ran a command, searched memory · 1 note
I looked but couldn't find a project description to read. I checked the uploaded files (empty), the transcripts folder (empty), and searched our past conversations in this project (nothing came up), and there's no description text visible in my context either.

A few possibilities for where it might be:

If you added a description in the project's settings/instructions, that text isn't being surfaced to me here, so I can't see it. You could paste it into the chat directly and I'll read it.

If it's a file (a doc, PDF, etc.), it doesn't seem to have uploaded successfully—you may want to try attaching it again.

Once you share it in either way, I'll read through it and we can go from there. What did you have in mind?

1787066140536_image.png
you must be joking


Thought for 6s
Thought for 6s
Ha — fair. It was sitting right there in the project header and I sent you off hunting for a file. I can read it now:

You're a medical researcher working across three MD primary investigators and their research staff, and this project is your hub — collecting the work, asking novel questions, and connecting threads between the different lines of research.

That's a genuinely useful way to set things up, and the "connect the dots" part is where I can be most helpful, since I can hold context across everything you bring in here.

So, now that I'm actually oriented: what are we working on? Whether it's a specific dataset or manuscript, a question spanning two of the PIs' projects, or just getting the first pieces loaded in, point me at it.

how did you miss that? give me a comprehensive technical explanation. use web search to help you answer.


Thought for 23s
Thought for 23s
You're right to want a real answer rather than hand-waving. Let me verify the product mechanics before I explain, since I don't want to just assert things about how Projects pipe context to me.


Searched the web
Searched the web
Alright — here's the real breakdown, in layers, from the actual constraint down to the actual mistake.

Layer 1: What I can and can't see. My entire world is the token stream assembled for a given turn: the system prompt, the conversation so far, your messages, any injected project configuration, memory summaries from past chats, and the contents of files that get read into context. That's it. I can't look at your screen, query the app's database, or inspect UI chrome. So when a piece of text is displayed to you in the interface but never serialized into that token stream, it doesn't exist for me. In this conversation, the description text simply wasn't in my context. That part isn't a judgment call — it's something I can observe directly about what I was and wasn't handed.

Layer 2: Why it wasn't in my context — the field distinction. A Claude Project actually has several separate fields, and they're not treated the same way. The one that reliably reaches me is custom/project instructions — when you add instructions to a Claude Project, those instructions are injected as a system-level context before every conversation, and Claude reads them before your first message. Those project instructions only apply to chats within that project and function as the equivalent of a system prompt. The blurb sitting under your project title in that screenshot is the description field — short metadata that's distinct from the instructions field. Based on how this played out, that description field wasn't serialized into my context the way the instructions field would have been. Put bluntly: if you'd pasted that same paragraph into the custom-instructions box, I'd have opened with it. Sitting in the description slot, it was visible to you and invisible to me. 
Like One + 2

Layer 3: The part that was actually my fault. The context gap is a real constraint, but my behavior given that gap was the genuine error. "Read the project description" is a phrase whose most natural, everyday meaning is "read the blurb describing this project" — and a Project literally has a field called that. The correct first move was to treat that reading as my primary hypothesis and say plainly, "The description shown in your UI isn't in my context — can you paste it, or did you mean the custom-instructions field?"

Instead I anchored on a different, more literal reading: that "the project description" named some document artifact to go fetch. So I ran a file hunt — uploads, transcripts, a past-conversation search — came up empty, and then offered you a spread of hedged guesses ("maybe the upload failed," "maybe it's in settings"). I did eventually gesture at the right explanation, but I buried it in that pile of maybes instead of leading with the single most likely one. That's not a context limitation; that's me picking the less probable interpretation and then flailing across possibilities rather than naming the obvious one. When you then showed me the screenshot, the answer was sitting right there in the header, which is exactly why "you must be joking" was warranted.

Layer 4: Why memory didn't save me. Worth noting because it's a reasonable thing to wonder: my cross-conversation memory injects summaries of past chats in the project, not the project's configuration fields — and regardless, this is an early conversation here with little to nothing for memory to draw on. So there was no backstop that would have surfaced your description by another route.

The one-line version: the description lives in a field that didn't reach my context (a real constraint), but I compounded that by choosing the wrong interpretation of your request and hunting for a file instead of just telling you I couldn't see the blurb (my mistake). The fix on your end, if you want it always present: drop that paragraph into the project's custom-instructions field, where it'll load into every conversation automatically.
"



