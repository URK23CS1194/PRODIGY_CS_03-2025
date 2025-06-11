```
def compute_strength(password_text):
    score = 0
    if len(password_text) >= 8:
        score += 1
    if any(c.islower() for c in password_text):
        score += 1
    if any(c.isupper() for c in password_text):
        score += 1
    if any(c.isdigit() for c in password_text):
        score += 1
    if any(c.isascii() and not c.isalnum() for c in password_text):
        score += 1
    return score
def strength_category(score):
    categories = {
        0: "Unacceptable",
        1: "Very Weak",
        2: "Weak",
        3: "Moderate",
        4: "Strong",
        5: "Very Strong"
    }
    return categories.get(score, "Unknown")
def improvement_tip(score):
    tips = {
        0: "Start with at least eight characters.",
        1: "Include uppercase and lowercase letters.",
        2: "Add digits to increase strength.",
        3: "Use special characters for better security.",
        4: "Good. Make it even better with more variety.",
        5: "Excellent password. No changes needed."
    }
    return tips.get(score, "No advice available.")
def strength_percentage(score):
    return int((score / 5) * 100)
def initiate_analysis():
    print("Password Strength Evaluation")
    print("Enter your password:")
    user_input = input()
    score = compute_strength(user_input)
    level = strength_category(score)
    percent = strength_percentage(score)
    advice = improvement_tip(score)
    print("Strength Level:", level)
    print("Strength Percentage:", str(percent) + "%")
    print("Feedback:", advice)
initiate_analysis()

