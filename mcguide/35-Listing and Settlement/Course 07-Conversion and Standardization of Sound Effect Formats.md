--- 
front: 
hard: Getting Started 
time: 20 minutes 
--- 

# Conversion and specification of sound effect formats 

The Minecraft developer platform supports uploading gameplay components and map components. Developers can embed sound effect files in resource packages of both component types. Rich sound effects can enhance the player's sensory experience. 

Currently, the Bedrock Edition of Minecraft and the Java Edition of Minecraft support the OGG sound effect format, and the developer platform machine review package only supports .OGG format sound effect files. 

Generally speaking, OGG provides the same sound quality for a lower file size. That is, it provides higher quality for the same file size. If it is clear to listen at a reasonable bit rate, there is no easily noticeable loss compared to the original audio. 

The bit rate can represent the number of bits of continuous audio played per unit time. The higher the bit rate, the better the sound quality playback effect. Currently, the OGG format supported by the developer platform needs to be exported according to the following specifications: 

| Specification type | Specification restrictions | 
| -------- | ------------- | 
| Sound effect type | OGG format | 
| Bit rate | Less than or equal to 128 | 
| Sampling rate | Unlimited | 

Developers can use third-party software to convert and export audio formats. 

## Still have unresolved issues? 

You can feedback other issues through the developer FAQ at the top of the [Developer Platform](https://mcdev.webapp.163.com/#/square), or directly click [this link](https://mcdev.webapp.163.com/#/feedbackModal). The official will contact you through the developer platform internal message. 
