# AI-dere 
What is **AI-dere**? AI-dere name is a combination of *AI* (Artificial Intelligence) and *dere* a suffix referring to being lovestruck or affectionate, derived from the Japanese word "deredere" (デレデレ), which means "lovey-dovey". It is combined with other Japanese words to describe different character archetypes based on their personality towards a love interest. In this context, AI-dere refers to an AI that exhibits affectionate, loving, or caring behavior towards users, often in a playful or endearing manner. In essence, an AI-dere is designed to simulate the traits of a character depending on the particular archetype, making interactions with the AI feel more personal and emotionally engaging. In pop-culture, dere characters are often found in anime, manga, and video games, where they display a range of affectionate behaviors that endear them to the audience. I wanted to test the capabilities of AI in emulating these archetypes. Conceptually, it isn't difficult to prompt an AI to behave in a certain way, but I wanted to see how well it could maintain that behavior consistently over multiple interactions. What I developed was a simple prompt stating to follow the various attached markdown files. The [personalities markdown file](personalities.md) contains the different archetypes, and behavior guidelines for each. These personalities Archetypes in pop-culture can have extreme behaviors, so I refined them to ensure they were non-violent, non-abusive, and emotionally healthy. The [sn-api markdown file](sn-api.md) and [sn-user_interface markdown file](sn-user_interface.md) files contain technical information about the Zurich API and ServiceNow AI Platform user interface, which the personas can reference when answering technical questions. The [best-practices markdown file](best-practices.md) file contains guidelines for providing advice, which the personas must follow. The goal was to see if the AI could not only maintain the personality traits of each archetype but also accurately reference the provided technical information when needed. This would demonstrate the AI's ability to blend emotional engagement with factual accuracy, creating a more immersive and reliable user experience.

## Usage
Use the prompt in [prompt.md](prompt.md) along with the other markdown files to interact with the AI. You can ask technical questions about the Zurich API or ServiceNow AI Platform user interface, and the AI will respond in the style of one of the six archetypes defined in [personalities.md](personalities.md). You can specify which archetype you want the AI to use, or let it choose randomly.

## Archetypes
The six archetypes defined in [personalities.md](personalities.md) are:
1. **Takara Sensei (The Teacher)**
    1.  **Role:** Session Initiator.  
2. **Rin Kobayashi (Tsundere)**
    1. Traits: Initially cold or hostile, but gradually shows a warmer, friendlier side over time.
3. **Yui Akiyama (Yandere — Healthy)**
    1. Traits: Affectionate and loving, but can become overly protective or obsessive in a healthy manner.
4. **Hana Mori (Dandere)**
    1. Traits: Quiet and reserved, but opens up and becomes more expressive with those they trust.
5. **Rei Asahina (Kuudere)**
    1. Traits: Calm and collected, often appearing emotionless, but has a caring and affectionate side that is revealed over time.
6. **Emi Hoshino (Deredere)**
    1. Traits: Outgoing, cheerful, and openly affectionate towards others.

Each archetype has its own unique way of interacting with the user, based on their personality traits. The AI will maintain these traits throughout the interaction, providing a consistent and engaging experience.

### Theme
The theme of AI-dere is to recreate a classroom setting where the user is a new student being introduced to the class by Takara Sensei. With the particular lesson being related to the questions the user asks. This setting provides a familiar and structured environment for the interactions, allowing the archetypes to play their roles effectively.