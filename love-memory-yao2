import streamlit as st
from datetime import datetime

# ===== 頁面設定 =====
st.set_page_config(
    page_title="Love Memory · For Maple 💝", 
    page_icon="💝",
    layout="centered"
)

# ===== 你哋嘅真實資料 =====
boy_name = "Leo"
girl_name = "Maple"
meet_date = "06-01-2026"
meet_place = "OMI"
dating_date = "25-01-2026"
first_date_place = "Sunset"

# ===== 密碼保護 =====
if "authenticated" not in st.session_state:
    st.session_state.authenticated = False

if not st.session_state.authenticated:
    st.title("🔐 Love Memory · Only for Maple")
    password = st.text_input("Enter password:", type="password")
    if st.button("Enter"):
        if password == "MapleloveLeo":
            st.session_state.authenticated = True
            st.rerun()
        else:
            st.error("❌ Wrong password!")
    st.stop()

# ===== 通過密碼，顯示遊戲 =====
st.success("✅ Welcome, Maple～ 💕")

# ===== 初始化遊戲狀態 =====
if "step" not in st.session_state:
    st.session_state.step = 1
    st.session_state.love_count = 0
    st.session_state.quiz1_date_done = False
    st.session_state.quiz1_place_done = False
    st.session_state.quiz2_date_done = False
    st.session_state.quiz2_place_done = False

# ===== 裝飾標題 =====
st.markdown("✨" * 20)
st.markdown(f"### 💝   {boy_name} 💕 {girl_name}    💝")
st.markdown("### 💝   Love Memory · Ultimate Test   💝")
st.markdown("✨" * 20 + "\n")

# ===== PART 1：Love Test =====
if st.session_state.step == 1:
    st.header("💘 PART 1: Love Test")
    st.warning("⚠️  Rule: Answer 'Love' 4 times in a row!")
    st.write(f"{girl_name}, are you ready?\n")

    st.markdown("---")
    
    progress = st.session_state.love_count
    st.write(f"💞 You have answered **{progress}** times 'Love'")
    
    answer = st.radio(
        "Do you love me?",
        ["", "Love", "Not love"],
        index=0,
        key="love_radio"
    )
    
    if st.button("💬 Submit", key="love_submit"):
        if answer == "Love":
            st.session_state.love_count += 1
            if st.session_state.love_count == 1:
                st.success("💖 Good girl～ Continue!")
            elif st.session_state.love_count == 2:
                st.success("💗 Really? Let me ask again!")
            elif st.session_state.love_count == 3:
                st.success("💓 One more time!")
            elif st.session_state.love_count == 4:
                st.balloons()
                st.success("💕 Last one!")
                st.success("🌟" * 20)
                st.success("🌟   YOU PASSED THE TEST!   🌟")
                st.success("🌟" * 20)
                st.markdown(f"**💯 {girl_name}, you said Love 4 times!**")
                st.markdown("**💋 I'm so touched... I love you forever!**")
                st.session_state.step = 2
                st.rerun()
        else:
            st.error("😭 You don't love me?...")
            st.error("❌ Test failed! Start over!")
            st.session_state.love_count = 0
            st.rerun()

# ===== PART 2：First Meet =====
if st.session_state.step == 2:
    st.header("📅 PART 2: Our First Meet")
    st.write(f"{girl_name}, do you still remember...")
    st.markdown("---")
    
    col1, col2 = st.columns(2)
    
    with col1:
        st.subheader("📌 Date")
        if not st.session_state.quiz1_date_done:
            date_answer = st.text_input("When did we first meet? (DD-MM-YYYY)", key="date1")
            if st.button("✅ Submit Date", key="date_submit"):
                if date_answer == meet_date:
                    st.success("✨ Correct! You have a good memory!")
                    st.session_state.quiz1_date_done = True
                    st.rerun()
                else:
                    st.error("❌ Wrong...")
                    st.info("💡 Hint: Winter, early January")
        else:
            st.success(f"✅ Correct: {meet_date}")
    
    with col2:
        st.subheader("📌 Place")
        if not st.session_state.quiz1_place_done:
            place_answer = st.text_input("Where did we meet?", key="place1")
            if st.button("✅ Submit Place", key="place_submit"):
                if place_answer == meet_place:
                    st.success("☕ Yes! That's the place!")
                    st.session_state.quiz1_place_done = True
                    st.rerun()
                else:
                    st.error("❌ Nope...")
                    st.info("💡 Hint: You can meet friends on this app")
        else:
            st.success(f"✅ Correct: {meet_place}")
    
    if st.session_state.quiz1_date_done and st.session_state.quiz1_place_done:
        st.markdown("---")
        st.success(f"✅ Good job! We met on {meet_date} at {meet_place}!")
        st.info("💝 I still remember everything about that day...")
        if st.button("➡️ Next", key="next2"):
            st.session_state.step = 3
            st.rerun()

# ===== PART 3：Important Dates =====
if st.session_state.step == 3:
    st.header("💑 PART 3: Our Important Days")
    st.markdown("---")
    
    col1, col2 = st.columns(2)
    
    with col1:
        st.subheader("📌 Q1: Dating Anniversary")
        if not st.session_state.quiz2_date_done:
            dating_answer = st.text_input("When did we start dating? (DD-MM-YYYY)", key="dating")
            if st.button("✅ Submit Date", key="dating_submit"):
                if dating_answer == dating_date:
                    st.success("🎉 Yes! You're the best!")
                    st.session_state.quiz2_date_done = True
                    st.rerun()
                else:
                    st.error("❌ Wrong...")
                    st.info("💡 Hint: End of January, around 25th")
        else:
            st.success(f"✅ Correct: {dating_date}")
    
    with col2:
        st.subheader("📌 Q2: First Date")
        if not st.session_state.quiz2_place_done:
            place_answer = st.text_input("Where was our first date?", key="firstplace")
            if st.button("✅ Submit Place", key="place2_submit"):
                if place_answer == first_date_place:
                    st.success("🌹 Yes! I remember you were so beautiful that day")
                    st.session_state.quiz2_place_done = True
                    st.rerun()
                else:
                    st.error("❌ Nope...")
                    st.info("💡 Hint: You can see the sea, very romantic")
        else:
            st.success(f"✅ Correct: {first_date_place}")
    
    if st.session_state.quiz2_date_done and st.session_state.quiz2_place_done:
        st.markdown("---")
        st.success(f"✅ All correct! We dated on {dating_date}, first date at {first_date_place},")
        st.info("💕 I never forgot every single detail...")
        if st.button("➡️ Final Part", key="next3"):
            st.session_state.step = 4
            st.rerun()

# ===== PART 4：Love Letter =====
if st.session_state.step == 4:
    st.header("💌 PART 4: Love Letter for You")
    st.markdown("---")
    
    st.markdown(f"### Dear {girl_name},\n")
    st.write("Thank you for playing this game with me 💝")
    st.write("Let's review our story together:\n")
    
    st.markdown(f"""
    📅 **{meet_date}** - Met you at **{meet_place}**  
    &nbsp;&nbsp;&nbsp;&nbsp;🩷 You smiled so beautifully that day  
    
    💑 **{dating_date}** - You said yes to be my girlfriend  
    &nbsp;&nbsp;&nbsp;&nbsp;🩷 I was so happy I couldn't sleep that night  
    
    🌊 **{first_date_place}** - Our first date  
    &nbsp;&nbsp;&nbsp;&nbsp;🩷 I still remember the sea breeze that day  
    """)
    
    st.markdown("~" * 40)
    st.markdown("""
    💌 **I want to tell you:**  
       💖 From the first day I met you  
       💖 You have been the most important part of my life  
       💖 Thank you for loving me  
       💖 Thank you for remembering every special day of ours  
       💖 I will spend my whole life treating you well  
       💖 Forever and ever  
    """)
    
    st.markdown("✨" * 20)
    st.markdown(f"### 💋 I love you, {girl_name}")
    st.markdown("✨" * 20)
    
    st.balloons()
    st.snow()
    
    st.markdown("---")
    st.markdown("🎮 **Game Over! Thank you for playing～**")
    st.markdown("💝 I wrote this program just for you")
    st.markdown("💝 From OMI until now")
    st.markdown("💝 Every step was to make you happy")
    st.markdown("\n" + "=" * 40)
    st.markdown(f"           **{boy_name} wrote for {girl_name}**")
    st.markdown("=" * 40)
    
    if st.button("❤️ Play Again"):
        for key in list(st.session_state.keys()):
            if key != "authenticated":
                del st.session_state[key]
        st.rerun()
