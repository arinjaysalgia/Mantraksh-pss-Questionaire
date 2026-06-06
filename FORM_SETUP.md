# Google Forms Setup Guide

## Step 1: Create English Form

Go to https://forms.google.com → Blank form

### Hidden fields (pre-filled via URL, user won't see these):
These fields will be auto-filled from the landing page. Add them as "Short answer" questions and mark as required:

1. **Name** (Short answer)
2. **Age** (Short answer)
3. **Phone** (Short answer)
4. **MID** (Short answer)
5. **City** (Short answer)
6. **State** (Short answer)
7. **Sessions Attended** (Short answer)
8. **Language** (Short answer)

### Rating Questions (1-10 Linear Scale):

> **Q1:** How would you rate your overall experience of the program?
> (1 = Very Poor, 10 = Excellent)

> **Q2:** How effective were the breathing techniques taught during the sessions?
> (1 = Not Effective, 10 = Highly Effective)

> **Q3:** How much improvement did you notice in your stress levels after the sessions?
> (1 = No Improvement, 10 = Significant Improvement)

> **Q4:** How would you rate the quality of instruction provided?
> (1 = Very Poor, 10 = Excellent)

> **Q5:** How likely are you to continue practicing the techniques learned?
> (1 = Very Unlikely, 10 = Definitely Will)

> **Q6:** How would you rate the impact on your sleep quality?
> (1 = No Impact, 10 = Major Improvement)

> **Q7:** How would you rate the impact on your emotional well-being?
> (1 = No Impact, 10 = Major Improvement)

> **Q8:** How comfortable was the session environment?
> (1 = Very Uncomfortable, 10 = Very Comfortable)

> **Q9:** How well did the program meet your expectations?
> (1 = Did Not Meet, 10 = Exceeded Expectations)

> **Q10:** How likely are you to recommend this program to others?
> (1 = Very Unlikely, 10 = Definitely Will)

---

## Step 2: Create Hindi Form

Same structure, Hindi translations:

### Rating Questions:

> **Q1:** कार्यक्रम के अपने समग्र अनुभव को आप कैसे आंकेंगे?
> (1 = बहुत खराब, 10 = उत्कृष्ट)

> **Q2:** सत्रों के दौरान सिखाई गई श्वास तकनीकें कितनी प्रभावी थीं?
> (1 = प्रभावी नहीं, 10 = अत्यधिक प्रभावी)

> **Q3:** सत्रों के बाद आपके तनाव स्तर में कितना सुधार हुआ?
> (1 = कोई सुधार नहीं, 10 = महत्वपूर्ण सुधार)

> **Q4:** दिए गए निर्देशों की गुणवत्ता को आप कैसे आंकेंगे?
> (1 = बहुत खराब, 10 = उत्कृष्ट)

> **Q5:** सीखी गई तकनीकों का अभ्यास जारी रखने की कितनी संभावना है?
> (1 = बहुत कम संभावना, 10 = निश्चित रूप से करूँगा/करूँगी)

> **Q6:** आपकी नींद की गुणवत्ता पर कितना प्रभाव पड़ा?
> (1 = कोई प्रभाव नहीं, 10 = बहुत सुधार)

> **Q7:** आपकी भावनात्मक स्थिति पर कितना प्रभाव पड़ा?
> (1 = कोई प्रभाव नहीं, 10 = बहुत सुधार)

> **Q8:** सत्र का वातावरण कितना सहज था?
> (1 = बहुत असहज, 10 = बहुत सहज)

> **Q9:** कार्यक्रम ने आपकी अपेक्षाओं को कितना पूरा किया?
> (1 = पूरा नहीं किया, 10 = अपेक्षाओं से अधिक)

> **Q10:** आप इस कार्यक्रम को दूसरों को सुझाने की कितनी संभावना रखते हैं?
> (1 = बहुत कम संभावना, 10 = निश्चित रूप से सुझाऊँगा/सुझाऊँगी)

---

## Step 3: Get Pre-fill URLs & Entry IDs

For EACH form:

1. Click the **⋮** menu (top right) → **Get pre-filled link**
2. Fill in dummy data for every field
3. Click **Get link** → **Copy link**
4. The URL looks like:
   ```
   https://docs.google.com/forms/d/e/FORM_ID/viewform?usp=pp_url&entry.123456=John&entry.789012=25...
   ```
5. Extract:
   - **Base URL**: everything before the `?` → put in `FORM_URLS.english` or `FORM_URLS.hindi`
   - **Entry IDs**: the `entry.XXXXXX` numbers → put in `ENTRY_IDS` object

## Step 4: Update index.html

Replace the placeholder values in `index.html`:

```javascript
const FORM_URLS = {
    english: 'https://docs.google.com/forms/d/e/YOUR_ENGLISH_ID/viewform',
    hindi: 'https://docs.google.com/forms/d/e/YOUR_HINDI_ID/viewform'
};

const ENTRY_IDS = {
    name: 'entry.123456789',
    age: 'entry.234567890',
    // ... etc
};
```

## Step 5: Deploy to Vercel

```bash
cd PSS_Questionaire
npm i -g vercel    # if not installed
vercel             # follow prompts, pick defaults
```

Done! Share the Vercel URL with participants.

---

## Tips for 500-600 Concurrent Users

- Google Forms handles this easily — no scaling concerns
- Pre-filled fields mean users only tap ratings — faster completion
- Both forms auto-save to Google Sheets for analysis
- Consider making the form "Limit to 1 response" OFF (some may share phones)



#### Googleform ublished link
- English : https://docs.google.com/forms/d/e/1FAIpQLSeFRHH5WN0k3T9WZALpeKvypfJ3y_t0PXEVewLUokXHHk40bg/viewform?usp=publish-editor