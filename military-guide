
import streamlit as st

# ==========================================
# 1. 프로그램 기본 설정
# ==========================================

st.set_page_config(
    page_title="군사 무기류 위험도 분석 및 안전 가이드",
    page_icon="🛡️",
    layout="wide"
)

st.title("🛡️ 군사 무기류 위험도 분석 및 위급상황 대처 가이드")

st.write(
    "군사 무기류와 관련된 사고의 위험성을 알아보고 "
    "위급상황 발생 시 안전하게 대처하기 위한 예방 가이드입니다."
)

st.warning(
    "본 프로그램의 점수는 교육용 참고 수치이며, "
    "실제 사고 발생 확률이나 전문적인 위험 평가를 의미하지 않습니다."
)


# ==========================================
# 2. 데이터 구조 (딕셔너리 및 리스트)
# ==========================================

weapon_data = {
    "총기류": {
        "risk": 9,
        "description": "인명 피해 가능성이 매우 높은 위험 유형입니다.",
        "scenarios": [
            {
                "name": "총기 관련 불발 사고",
                "risk": 3,
                "advice": "총기에 접근하거나 만지지 말고 안전한 거리로 이동한 뒤 112에 신고합니다."
            },
            {
                "name": "총기 난사 및 위협 상황",
                "risk": 5,
                "advice": "위험 지역에서 즉시 벗어나고, 탈출이 어렵다면 안전한 장소에 숨어 112에 신고합니다."
            },
            {
                "name": "총기 오작동 의심 상황",
                "risk": 4,
                "advice": "총기를 직접 확인하거나 조작하지 말고 주변 사람의 접근을 막은 뒤 관계 기관에 신고합니다."
            }
        ]
    },

    "폭발물류": {
        "risk": 10,
        "description": "폭발 및 파편으로 심각한 인명 피해가 발생할 수 있는 위험 유형입니다.",
        "scenarios": [
            {
                "name": "의심스러운 폭발물 발견",
                "risk": 5,
                "advice": "물체에 접근하거나 만지지 말고 주변 사람을 대피시킨 뒤 112에 신고합니다."
            },
            {
                "name": "폭발 사고 발생",
                "risk": 5,
                "advice": "폭발 지점과 잔해에서 멀어지고 추가 폭발 가능성을 고려해 안전한 곳으로 대피합니다."
            },
            {
                "name": "폭발물 의심 물체 발견 후 위협",
                "risk": 4,
                "advice": "물체를 이동하거나 확인하지 말고 안전한 거리에서 관계 기관의 안내를 기다립니다."
            }
        ]
    },

    "유해가스류": {
        "risk": 9,
        "description": "흡입 및 신체 접촉으로 심각한 건강 피해가 발생할 수 있는 위험 유형입니다.",
        "scenarios": [
            {
                "name": "정체불명의 가스 누출",
                "risk": 4,
                "advice": "가스가 의심되는 장소에서 벗어나 신선한 공기가 있는 안전한 장소로 이동합니다."
            },
            {
                "name": "유해가스 노출 의심",
                "risk": 5,
                "advice": "즉시 노출 장소를 벗어나고 119에 신고합니다. 직접 구조를 시도하지 않습니다."
            },
            {
                "name": "밀폐 공간 내 가스 사고",
                "risk": 5,
                "advice": "밀폐 공간에 다시 들어가지 말고 외부의 안전한 장소에서 구조기관의 도움을 요청합니다."
            }
        ]
    }
}


# ==========================================
# 3. 위험도 분석 함수
# ==========================================

def analyze_risk(weapon):

    risk = weapon_data[weapon]["risk"]

    if risk >= 9:
        level = "매우 높음"
        message = "매우 높은 위험 수준입니다. 각별한 주의가 필요합니다."

    elif risk >= 7:
        level = "높음"
        message = "높은 위험 수준입니다. 안전거리를 유지해야 합니다."

    elif risk >= 4:
        level = "보통"
        message = "주의가 필요한 위험 수준입니다."

    else:
        level = "낮음"
        message = "상대적으로 낮은 위험 수준입니다."

    return risk, level, message


# ==========================================
# 4. 시뮬레이션 출력 함수
# ==========================================

def show_simulation(weapon):

    scenarios = weapon_data[weapon]["scenarios"]

    st.subheader("🚨 대표 위급상황 및 대처요령")

    st.write(
        weapon + "에 관한 대표적인 사고 상황 3가지와 "
        "일반인을 위한 안전 대처요령입니다."
    )

    # 사고 상황 표 생성
    simulation_list = []

    for i in range(len(scenarios)):

        simulation_list.append({
            "구분": "시뮬레이션 " + str(i + 1),
            "사고 유형": scenarios[i]["name"],
            "위험도": str(scenarios[i]["risk"]) + "점",
            "대처요령": scenarios[i]["advice"]
        })

    st.table(simulation_list)

    # 위험도 결과 확인
    st.subheader("📊 상황별 위험도 분석")

    for i in range(len(scenarios)):

        risk = scenarios[i]["risk"]

        st.write(
            "시뮬레이션 " + str(i + 1) +
            " : " + str(risk) + "점 / 5점"
        )

        if risk >= 5:
            st.error("고위험 상황 - 즉각적인 대피 및 신고가 필요합니다.")

        elif risk >= 3:
            st.warning("주의 상황 - 안전거리 확보 및 관계 기관 신고가 필요합니다.")

        else:
            st.info("상황을 주의 깊게 확인하고 안전을 확보해야 합니다.")


# ==========================================
# 5. 무기류 선택 화면
# ==========================================

st.divider()

st.subheader("1. 분석할 무기류 선택")

weapon_list = ["총기류", "폭발물류", "유해가스류"]

selected_weapon = st.selectbox(
    "무기류 종류를 선택하세요.",
    weapon_list
)


# ==========================================
# 6. 위험도 분석 버튼
# ==========================================

if st.button("🔍 위험도 분석", use_container_width=True):

    st.session_state["selected_weapon"] = selected_weapon
    st.session_state["analysis_done"] = True
    st.session_state["simulation_done"] = False


# ==========================================
# 7. 위험도 분석 결과 출력
# ==========================================

if st.session_state.get("analysis_done", False):

    weapon = st.session_state["selected_weapon"]

    risk, level, message = analyze_risk(weapon)

    st.divider()

    st.subheader("2. 위험도 분석 결과")

    st.write(
        "다음 무기류에 대한 위험도 분석 결과입니다."
    )

    # 위험도 표
    result_table = [{
        "무기류": weapon,
        "위험도": str(risk) + "점",
        "위험 수준": level
    }]

    st.table(result_table)

    st.write(weapon_data[weapon]["description"])

    # 위험도 강조
    if risk >= 9:
        st.error("🚨 고위험 경고 : " + str(risk) + "점 / 10점")

    elif risk >= 7:
        st.warning("⚠️ 위험 경고 : " + str(risk) + "점 / 10점")

    else:
        st.info("위험도 : " + str(risk) + "점 / 10점")

    st.write(message)

    # ======================================
    # 8. 위급상황 시뮬레이션 버튼
    # ======================================

    st.divider()

    if st.button("🚨 위급사항 시뮬레이션", use_container_width=True):

        st.session_state["simulation_done"] = True

    if st.session_state.get("simulation_done", False):

        show_simulation(weapon)


# ==========================================
# 9. 하단 안내
# ==========================================

st.divider()

st.caption(
    "본 프로그램은 안전교육 및 사고 예방을 위한 교육용 가이드입니다."
)

st.caption(
    "실제 긴급상황에서는 112(경찰) 또는 119(소방·구급)에 신고하고 "
    "현장 관계자의 안내를 따르세요."
)
