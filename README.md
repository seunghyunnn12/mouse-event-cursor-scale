# mouse-event-cursor-scale
🎨 Custom Cursor Animation

📌 프로젝트 소개

이 프로젝트는 GSAP을 활용하여 커스텀 마우스 커서를 적용하고, 특정 요소에 마우스를 올릴 때 다양한 애니메이션 효과를 주는 기능을 포함합니다.

🚀 주요 기능

커스텀 커서(.cursor-wrap)가 마우스를 따라 이동

링크(<a>), 버튼(<button>) 위에서 커서 크기가 작아짐

특정 요소(.mouse-event)에 마우스를 올리면 .learn-more 텍스트 표시

🛠️ 사용된 기술

GSAP (GreenSock Animation Platform)

gsap.to() → 부드러운 애니메이션 적용

gsap.timeline() → 타임라인 애니메이션 활용

mouseenter, mouseleave 이벤트 활용

📜 코드 주요 내용

// 마우스 이동 시 커스텀 커서 위치 변경
document.addEventListener('mousemove', function (e) {
    gsap.to(customCursor, {
        x: e.clientX,
        y: e.clientY,
        xPercent: -50,
        yPercent: -50,
        duration: .1,
        opacity: 1
    })
})

// 링크 및 버튼 위에서 커서 크기 축소
const clickableElements = document.querySelectorAll('a,button')
clickableElements.forEach((el) => {
    el.addEventListener('mouseenter', () => {
        gsap.to(customCursor2, { scale: .3, duration: .1 })
    })
    el.addEventListener('mouseleave', () => {
        gsap.to(customCursor2, { scale: 1, duration: .1 })
    })
})

// 특정 요소 위에서 `.learn-more` 텍스트 표시
const mouseTl = gsap.timeline({ paused: true })
mouseTl.to('.cursor-wrap .learn-more', { opacity: 1, duration: .1 })

document.querySelectorAll('.mouse-event').forEach((el) => {
    el.addEventListener('mouseenter', () => mouseTl.play())
    el.addEventListener('mouseleave', () => mouseTl.reverse())
})

