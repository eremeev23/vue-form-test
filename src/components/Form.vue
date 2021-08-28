<template>
    <div class="form ">
        <div class="form__conteiner">
        <form action="https://script.google.com/macros/s/AKfycbwT5P8_PkFBy_vM5bhb_b-GsxQv7__15YilhVuzruB-JcFa1XXAp3kFS5_Y8a2lqg3K5A/exec" @submit.prevent="" class="test">
            <!-- Block 1 -->
            <div class="block block-1" :class="{'filled': filled1}">
                <div class="input">
                    <input type="text" autocomplete="none" v-model="formData.name" id="name" name="name" class="input__name required" required>
                    <label class="label" for="name"> <span class="content-label">Имя</span></label>
                </div>

                <div class="input">
                    <input type="text" autocomplete="none" v-model="formData.telegram" id="telegram" name="telegram" class="input__tg required" required>
                    <label class="label" for="name"><span class="content-label">Ник в Telegram</span></label>
                </div>

                <div class="input">
                    <input type="url" autocomplete="none" v-model="formData.repo" id="repo" name="repo" class="input__git required" required>
                    <label class="label" for="name"> <span class="content-label">Ссылка на репозиторий формы </span></label>
                </div>

                <div class="input input__q1">
                    <input type="text" autocomplete="none" v-model="formData.qNotWantedActivity" id="qNotWantedActivity" name="qNotWantedActivity" class="input__q1 required" required>
                    <label class="label" for="name"><span class="content-label">Что вы точно не хотите делать в работе, что вы делаете с неохотой? </span></label>
                </div>
            </div>
            <!-- Block 2 -->
            <div class="block block-2" :class="{'filled': filled2}">
                <p class="question">Как вы оцениваете свою способность взаимодействовать с дизайном?</p>
                <p class="comment"> А именно, работа с векторами, внимательность к деталям, возможность проявить инициативу - например, можете ли сверстать макет адаптируя его для мобильных устройств с макета под десктоп?</p>
                
                <label class="label__question-l" for="qDesign ">0</label>
                <input @input="sliderMove" type="range" id="qDesign" class="range__question1" name="qDesign" step="1" min="0%" max="100" value="50">
                <label class="label__question-r" for="qDesign ">100%</label>
                <div class="slider__value"><span class="slider-1">50%</span></div>
                <div class="slider-line-1"></div>
                
                <div class="input input__block-2">
                    <input type="text" autocomplete="none" id="qDesignComment" name="qDesignComment" class="input input__comm">
                    <label class="label" for="qDesignComment"> <span class="content-label"> Ваш комментарий (по желанию) </span></label>
                </div>
            </div>
            <!-- Block 3 -->
            <div class="block block-3" :class="{'filled': filled3}">
                <p class="question">Готовы ли работать с CSS анимацией?</p>
                <p class="comment">Часто нужна несложная CSS анимация без сторонних библиотек для сопровождения какого-либо действия или плавной подачи информации, но без фанатизма</p>
                
                <label class="label__question-l-2" for="qCssAnimation">0</label>
                <input @input="sliderMoveTwo" type="range" id="qCssAnimation" class="range__question2" name="qCssAnimation" step="1" min="0%" max="100" value="50">
                <label class="label__question-r-2" for="qCssAnimation">100%</label>
                <div class="slider__value"><span class="slider-2">50%</span></div>
                <div class="slider-line-2"></div>
                
                <div class="input input__block-2">
                    <input type="text" autocomplete="none" id="qCssAnimationComment" name="qCssAnimationComment" class="input input__comm">
                    <label class="label" for="qCssAnimationComment"><span class="content-label">Ваш комментарий (по желанию)</span></label>
                </div>
            </div>
            <!-- Block 4 -->
            <div class="block block-4" :class="{'filled': filled4}">
                <div class="input">
                    <input type="text" autocomplete="none" v-model="formData.qChores" id="qChores" name="qChores" class="input required" required>
                    <label class="label" for="qChores"> <span class="content-label">Как вы относитесь к рутинной работе? </span></label>
                </div>
            </div>
            <!-- Block 5 -->
            <div class="block block-5" :class="{'filled': filled5}">
                <div class="input input__block-5">
                    <input type="text" autocomplete="none" v-model="formData.qFreelance" id="qFreelance" name="qFreelance" class="input__freelance required " required>
                    <label class="label" for="qFreelance "><span class="content-label"> Готовы ли посвятить все 100% своего времени на работу с нашими задачами, не отвлекаясь на стороннуюю разработку? </span></label>
                </div>
            </div>
            <button type="submit" @click="submitForm" class="btn">Отправить</button>
        </form>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Form',
    data() {
        return {
            filled1: false,
            filled2: false,
            filled3: false,
            filled4: false,
            filled5: false,
            formData: {
                name: '',
                telegram: '',
                repo: '',
                qNotWantedActivity: '',
                qDesign: '0',
                qCssAnimation: '0',
                qChores: '',
                qFreelance: ''
            }
        }
    },
    created() {
      window.addEventListener('click', this.fillBlock);
      this.fillBlock();
    },
    methods: {
        sliderMove() {
            const sliderValue = document.querySelector('.slider-1');
            const inputSlider = document.querySelector('.range__question1');
            const labelRight = document.querySelector('.label__question-r');
            const labelLeft = document.querySelector('.label__question-l');
            const sliderLine = document.querySelector('.slider-line-1');

            let value = inputSlider.value;
            sliderValue.textContent = value + "%";
            sliderValue.style = `left:${value}%`;
            sliderLine.style = `width:${value}%`;
            this.filled2 = true;
            if (value > 88) {
                labelRight.style = 'display: none'
            } else {
                labelRight.style = 'display: block'
            }
            if (value < 3) {
                labelLeft.style = 'display: none';
            } else {
                labelLeft.style = 'display: block'
            }
        },
        sliderMoveTwo() {
            const sliderValue = document.querySelector('.slider-2');
            const inputSlider = document.querySelector('.range__question2');
            const labelRight = document.querySelector('.label__question-r-2');
            const labelLeft = document.querySelector('.label__question-l-2');
            const sliderLine = document.querySelector('.slider-line-2');

            let value = inputSlider.value;
            sliderValue.textContent = value + "%";
            sliderValue.style = `left:${value}%`;
            sliderLine.style = `width:${value}%`;
            this.filled3 = true;
            if (value > 88) {
                labelRight.style = 'display: none'
            } else {
                labelRight.style = 'display: block'
            }
            if (value < 3) {
                labelLeft.style = 'display: none';
            } else {
                labelLeft.style = 'display: block'
            }
        },
        fillBlock() {
            const button = document.querySelector('.btn');
            if (this.formData.name && this.formData.telegram && this.formData.repo && this.formData.qNotWantedActivity) {
                this.filled1 = true;
            } else {
                this.filled1 = false;
            }
            if (this.formData.qChores) {
                this.filled4 = true;
            } else {
                this.filled4 = false;
            }
            if (this.formData.qFreelance) {
                this.filled5 = true;
            } else {
                this.filled5 = false;
            }
            if (this.filled1 && this.filled2 && this.filled3 && this.filled4 && this.filled5) {
                button.classList.add('ready');
            }
        },
        submitForm() {
            const button = document.querySelector('.btn');
            const form = document.querySelector('.form__conteiner');
            const blockOne = document.querySelector('.block-1');
            const blockTwo = document.querySelector('.block-2');
            const blockThree = document.querySelector('.block-3');
            const blockFour = document.querySelector('.block-4');
            const blockFive = document.querySelector('.block-5');
            if (this.filled1 == false) {
                blockOne.classList.add('unfilled-block')
            }
            if (this.filled2 == false) {
                blockTwo.classList.add('unfilled-block')
            }
            if (this.filled3 == false) {
                blockThree.classList.add('unfilled-block')
            }
            if (this.filled4 == false) {
                blockFour.classList.add('unfilled-block')
            }
            if (this.filled5 == false) {
                blockFive.classList.add('unfilled-block')
            }
            if (this.filled1 && this.filled2 && this.filled3 && this.filled4 && this.filled5){
                form.classList.add('submited');
                button.classList.add('done-btn');
                blockOne.classList.add('done');
                blockTwo.classList.add('done');
                blockThree.classList.add('done');
                blockFour.classList.add('done');
                blockFive.classList.add('done');
            }
        }
    },
}
</script>

<style scoped>
/* MAIN CONTEINER */
.form {
    display: flex;
    justify-content: center;
    min-height: 100vh;
}
.test {
    width: 520px;
    display: flex;
    align-items: flex-start;
    justify-content: start;
    flex-direction: column;
}
.form__conteiner{
    width: 540px;
}
/* BLOCKS */
.block {
    width: 100%;
    max-width: 520px;
    position: relative;
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    margin: 2px;
}
.block::after {
    content: '';
    position: absolute;
    left: 0;
    top: 0;
    width: 4px;
    height: 100%;
    background: #999999;
}
.block-2, .block-3 {
    height: 260px;
    display: block;
    text-align: left;
    padding-left: 7px;
}
.block-5 {
    position: relative;
    height: 120px;
}
.block-5 div {
    position: absolute;
    bottom: 0;
    height: 100%;
    margin: 0 6px;
}

/* INPUTS */
.input {
    height: 50px;
    width: 100%;
    position: relative;
    margin: 8px;
    overflow: hidden;
}
.input__q1 {
    height: 80px;
    padding-top: 18px;
}
.input input {
    padding-top: 3px;
    position: absolute;
    left: 0;
    height: 100%;
    width: 100%;
    font-size: 18px;
    outline: none;
    border: none;
    background: inherit;
}
.label {
    pointer-events: none;
    position: absolute;
    bottom: 0;
    left: 0px;
    width: 100%;
    height: 100%;
    text-align: left;
    border-bottom: 2px solid #999999;
}
.label::after {
    content: '';
    position: absolute;
    left: 0px;
    bottom: -2px;
    height: 100%;
    width: 100%;
    border-bottom: 3px solid #63EBF7;
    transform: translateX(-101%);
    transition: all .5s ease;
}
.unfilled {
    border-bottom: 3px solid #ff004c;
}
.content-label {
    position: absolute;
    bottom: 5px;
    left: 0px;
    transition: all .3s ease;
}
.input input:focus + .label .content-label,
.input input:valid + .label .content-label {
    transform: translateY(-100%);
    font-size: 14px;
    color: #63EBF7;
}
.input__q1 input:focus + .label .content-label,
.input__q1 input:valid + .label .content-label {
    transform: translateY(-190%);
    font-size: 14px;
    color: #63EBF7;
}
.input input:focus + .label::after,
.input input:valid + .label::after {
    transform: translateX(0);
}
.input__freelance {
    margin-top: 30px;
}

/* BUTTON */
.btn {
    padding: 0;
    margin-left: 2px;
    min-width: 528px;
    height: 8vh;
    cursor: pointer;
    text-transform: uppercase;
    font-size: 1.2em;
    border: none;
    color: #fff;
    background: #999999;
    transition: all .3s linear;
}
.btn:hover {
    background: #0fb900;
}

/* SLIDERS */
.question {
    font-weight: 600;
}
.comment {
    font-size: 14px;
    color: #999999;
}
.range__question1 {
    position: relative;
    outline: none;
    width: 100%;
    height: 1px;
    -webkit-appearance: none;
    background: black;
}
.range__question1::-webkit-slider-thumb {
    -webkit-appearance: none;
    width: 18px;
    height: 18px;
    border: 1px solid #000;
    border-radius: 50%;
    background: #63EBF7;
}
.range__question2 {
    position: relative;
    outline: none;
    width: 100%;
    height: 1px;
    -webkit-appearance: none;
    background: black;
}
.range__question2::-webkit-slider-thumb {
    -webkit-appearance: none;
    width: 18px;
    height: 18px;
    border: 1px solid #000;
    border-radius: 50%;
    background: #63EBF7;   
}
.slider__value {
    position: relative;
    width: 100%;
}
.slider__value span {
    position: absolute;
    height: 20px;
    width: 32px;
    color: #63EBF7;
    left: 50%;
    transform: translateX(-12%);
}
.label__question-r {
    position: absolute;
    right: 0;
    bottom: 52px;
    font-size: 14px;
}
.label__question-l {
    position: absolute;
    left: 8px;
    bottom: 52px;
    font-size: 14px;
}
.input__block-2 {
    margin-top: 20px;
    height: 60px;
}
.label__question-r-2 {
    position: absolute;
    right: 0;
    bottom: 80px;
    font-size: 14px;
}
.label__question-l-2 {
    position: absolute;
    left: 8px;
    bottom: 80px;
    font-size: 14px;
}

.slider-line-1 {
    z-index: 10;
    position: absolute;
    top: 67.5%;
    left: 9px;
    height: 1px;
    width: 50%;
    max-width: 519px;
    background: #63EBF7;
}
.slider-line-2 {
    position: absolute;
    top: 58%;
    left: 9px;
    height: 1px;
    width: 50%;
    max-width: 519px;
    background: #63EBF7;
}
/* STATUS */
.filled::after {
    background: #63EBF7;
}
.ready{
    background: #63EBF7;
}
.unfilled-block::after {
    background: #F40C53;
}
.done::after, .done-btn {
    background: #79ff0c;
}
.submited {
    background: rgb(233, 233, 233);
}
</style>