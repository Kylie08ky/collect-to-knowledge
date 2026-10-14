# Visual knowledge cards

Enable when explicitly requested or configured by the user. The host must provide
an image-generation capability; no image model or API key is bundled here.

1. Finish and source-check the concise card text first.
2. Use the user's reference style if provided. Otherwise suggest a readable
   portrait card: cream background, restrained pastel panels, strong title,
   one-sentence principle, a diagram/example, and a short action checklist.
3. Keep one visual card focused on a single useful method. Do not squeeze a full
   transcript onto the image or imply every text card needs a separate image.
4. Label hypothetical examples and assistant-designed actions. Include a brief
   source and honest coverage label, such as “automatic transcript summary”.
5. Inspect the generated image for text errors, numbers, formulas, truncation,
   readability, and source attribution. Correct material mistakes before delivery.
6. Keep the editable text version. Save the selected image in the host's
   user-facing output directory and provide its actual location.
7. If Notion saving is authorized, upload and embed the image in the same note.
   Verify the uploaded image block, not just a successful local file write.
8. If generation/upload is unavailable, deliver the text and optional image
   prompt, explicitly stating what is incomplete. Never claim to have generated
   or attached an image that does not exist.
