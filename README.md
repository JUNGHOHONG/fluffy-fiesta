import React, { useState } from "react";

const mbtiData = {
  ENFP: { dog: "푸들", description: "활발하고 창의적인 성격" },
  ENTJ: { dog: "보더콜리", description: "리더십이 강하고 영리함" },
  ESFJ: { dog: "골든 리트리버", description: "다정하고 친근함" },
  ISTP: { dog: "시바 이누", description: "독립적이고 신중함" },
  ESTP: { dog: "닥스훈트", description: "호기심 많고 용감함" },
  ISFJ: { dog: "코카스파니엘", description: "다정하고 충성심 강함" },
  ENTP: { dog: "허스키", description: "장난기 많고 자유로움" },
  ISTJ: { dog: "불독", description: "차분하고 신뢰할 수 있음" },
  ESFP: { dog: "비글", description: "사교적이고 유쾌함" },
  INTJ: { dog: "도베르만", description: "영리하고 보호 본능 강함" },
  INFP: { dog: "치와와", description: "감정이 풍부하고 애정 표현이 많음" },
  ESTJ: { dog: "래브라도 리트리버", description: "자신감 있고 책임감 강함" },
};

const DogMBTIApp = () => {
  const [selectedMBTI, setSelectedMBTI] = useState("");
  const [result, setResult] = useState(null);

  const handleCheckMBTI = () => {
    if (mbtiData[selectedMBTI]) {
      setResult(mbtiData[selectedMBTI]);
    } else {
      setResult(null);
    }
  };

  return (
    <div style={{ textAlign: "center", marginTop: "50px" }}>
      <h1>강아지 MBTI 추천</h1>
      <p>당신의 MBTI를 선택하면 어울리는 강아지를 추천해 드립니다!</p>
      <select onChange={(e) => setSelectedMBTI(e.target.value)}>
        <option value="">MBTI 선택</option>
        {Object.keys(mbtiData).map((mbti) => (
          <option key={mbti} value={mbti}>{mbti}</option>
        ))}
      </select>
      <button onClick={handleCheckMBTI}>추천 보기</button>

      {result && (
        <div style={{ marginTop: "20px" }}>
          <h2>추천 강아지: {result.dog}</h2>
          <p>{result.description}</p>
        </div>
      )}
    </div>
  );
};

export default DogMBTIApp;
