<template>
  <div class="wedding">
    <div class="intro">
      <div class="container">
        <div class="intro__header">
          <div class="intro__menu">
            <span>Приглашение</span>
            <span>Тайминг</span>
            <span>Локация</span>
          </div>
          <div class="intro__logo">
            <img src="@/assets/icons/logo_intro.png" alt="">
          </div>
          <div class="intro__menu">
            <span>Дресс-код</span>
            <span>Напитки</span>
            <span>Творчество</span>
          </div>
        </div>
        <div class="intro__date">25 октября 2025</div>
        <div class="intro__title">
          <div>Артур и Аннелия</div>
          <div>Свадебное торжество</div>
        </div>
      </div>
    </div>
    <div class="container">
      <div class="block">
        <div class="block__content">
          <div class="block__half">
            <img src="@/assets/img/flowers.jpg" alt="">
          </div>
          <div class="block__half">
            <div class="invite">Дорогие наши, родные и близкие!</div>
            <div class="block__text">
              25 октября 2025 года начинается вдохновляющая история новой семейной жизни.
              Нам хочется видеть вас на её первых страницах. Приглашаем разделить с нами радость
              свадебного торжества, окунуться в атмосферу любви и семейного праздника
            </div>
            <div class="names">
              <div>Артур, Аннелия</div>
              <div>Валерий, Луиза</div>
            </div>
            <div class="desc">
              Напишите, пожалуйста, в каком составе вы прибудете на торжество, укажите имя и
              фамилию,
              имена членов вашей семьи
            </div>
            <div class="form">
              <div class="form__title">Имена и фамилии гостей</div>
                <div class="form__textarea">
                  <img v-if="guestCome.names" @click="guestCome.names= ''"
                       src="@/assets/icons/cross.png" alt="">
                  <textarea v-model="guestCome.names"
                            placeholder="Например: Иванов Иван и Иванова Наталья"></textarea>
                </div>
                <div class="counter">
                  <div class="counter__title">Количество гостей</div>
                  <div class="counter__panel">
                    <img @click="deleteGuest(guestCome)" src="@/assets/icons/minus.png" alt="">
                    <div class="counter__value">{{ guestCome.count }}</div>
                    <img @click="addGuest(guestCome)" src="@/assets/icons/plus.png" alt="">
                  </div>
                </div>
                <button class="form__sub"
                        :class="{'form__sub_active': guestCome.count && guestCome.names}">
                  {{ dataSending.guestCome.btnText }}
                </button>
            </div>
          </div>
        </div>
      </div>
      <div class="block">
        <div class="block__header">Логотип свадьбы</div>
        <div class="block__content block__content_margin">
          <div class="block__half block__half_margin block__half_logo">
            <img src="@/assets/icons/logo_logo.png" alt="">
          </div>
          <div class="block__half">
            <div class="block__title">Две буквы «А»</div>
            <div class="block__text block__text_margin">Логотип Артура и Аннелии - две заглавные
              буквы «А», олицетворение имен жениха и невесты. Это - символ объединения двух
              личностей, двух жизней, двух судеб в один союз
            </div>
            <div class="block__title">Символ союза</div>
            <div class="block__text">Буквы не просто стоят рядом, они переплетаются. Это визуальное
              соединение букв символизирует союз и близость супругов. Брак — это не два отдельных
              человека, а новое, общее «мы». Переплетение говорит о доверии, поддержке, заботе друг
              о друге
            </div>
          </div>
        </div>
        <div class="block__content">
          <div class="block__half block__half_margin">
            <div class="block__title">Национальный орнамент - казахские корни</div>
            <div class="block__text block__text_margin">Левая буква «А» украшена традиционным
              казахским узором. Это отсылает к богатой культуре и наследию, корням семьи, это
              проявление уважения к своим истокам. Орнамент добавляет глубины в уникальность
              логотипа, вплетая в него символику родной земли
            </div>
            <div class="block__title">Мужское и женское начало</div>
            <div class="block__text">Правая буква «А» - строгая, прямая и мужественная,
              символизирует силу, опору, ответственность, воплощая Артура. Левая - более мягкая,
              изящная, украшенная, как нежность и красота Аннелии. Вместе они создают гармонию,
              баланс и завершенность
            </div>
          </div>
          <div class="block__half">
            <img src="@/assets/img/vostok.jpg" alt="">
          </div>
        </div>
      </div>
      <div class="block">
        <div class="block__header">Тайминг</div>
        <div class="block__sub-header">25 октября 2025</div>
        <div class="divider">
          <div class="divider__line"></div>
          <div class="block__content block__content_margin-s">
            <div class="block__half">
              <div class="timing">
                <img src="@/assets/icons/13.png" alt="">
                <div class="timing__item">
                  <div class="timing__time">13:30</div>
                  <div class="timing__line">
                    <div></div>
                    <div></div>
                  </div>
                  <div class="timing__event">начало сбора гостей</div>
                </div>
              </div>
            </div>
          </div>
          <div class="block__content block__content_margin-s">
            <div class="block__half">
            </div>
            <div class="block__half">
              <div class="timing">
                <div class="timing__item">
                  <div class="timing__time">14:00</div>
                  <div class="timing__line timing__line_reverse">
                    <div></div>
                    <div></div>
                  </div>
                  <div class="timing__event">национальный обряд «Беташар»</div>
                </div>
                <img src="@/assets/icons/14.png" alt="">
              </div>
            </div>
          </div>
          <div class="block__content block__content_margin-s">
            <div class="block__half">
              <div class="timing">
                <img src="@/assets/icons/14_20.png" alt="">
                <div class="timing__item">
                  <div class="timing__time">14:20</div>
                  <div class="timing__line">
                    <div></div>
                    <div></div>
                  </div>
                  <div class="timing__event">торжественная регистрация <br/> брака</div>
                </div>
              </div>
            </div>
          </div>
          <div class="block__content block__content_margin-s">
            <div class="block__half">
            </div>
            <div class="block__half">
              <div class="timing">
                <div class="timing__item">
                  <div class="timing__time">14:40</div>
                  <div class="timing__line timing__line_reverse">
                    <div></div>
                    <div></div>
                  </div>
                  <div class="timing__event">фотосессия молодоженов <br/> с гостями</div>
                </div>
                <img src="@/assets/icons/14_40.png" alt="">
              </div>
            </div>
          </div>
          <div class="block__content">
            <div class="block__half">
              <div class="timing">
                <img src="@/assets/icons/15_30.png" alt="">
                <div class="timing__item">
                  <div class="timing__time">15:30</div>
                  <div class="timing__line">
                    <div></div>
                    <div></div>
                  </div>
                  <div class="timing__event">начало банкета</div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="block">
        <div class="block__header">Локация</div>
        <div class="block__sub-header">«Олимпия» загородный клуб</div>
        <div class="block__content">
          <div id="map" class="block__half"></div>
          <div class="block__half">
            <img src="@/assets/img/location.jpg" alt="">
          </div>
        </div>
      </div>
      <div class="block">
        <div class="block__header">Цветовая палитра нашей свадьбы</div>
        <div class="block__content block__content_margin-s">
          <div class="block__half block__half_margin">
            <div class="block__text block__text_palita">
              Уважаемые гости, оформление праздника будет выполнено в гамме лёгкой золотой осени:
              бордо, тёплое золото, оливковый, шалфейно зелёные оттенки и прочие
            </div>
          </div>
          <div class="block__half">
            <div class="block__text block__text_palita">
              Мы будем признательны, если вы поддержите нашу атмосферу в выборе нарядов. Ниже
              представлены примеры цветов, которые помогут вам сориентироваться
            </div>
          </div>
        </div>
        <div class="palitra">
          <div class="palitra__item">
            <div class="palitra__text">Шалфейный <br/> зелёный</div>
          </div>
          <div class="palitra__item">
            <div class="palitra__text">Светло <br/> терракотовый</div>
          </div>
          <div class="palitra__item">
            <div class="palitra__text">Кофейный мокка <br/> мусс</div>
          </div>
          <div class="palitra__item">
            <div class="palitra__text">Кашемирово <br/> чёрный</div>
          </div>
          <div class="palitra__item">
            <div class="palitra__text">Ванильно <br/> бежевый</div>
          </div>
        </div>
      </div>
      <div class="block">
        <div class="block__header">
          Предпочтения по алкоголю
        </div>
        <div class="block__sub-header"
             :class="alcoStep.step ? 'block__sub-header_inactive' : 'block__sub-header_grey'">Шаг 1
          — Сколько человек из вашей компании <br/> будут пить алкогольные напитки?
        </div>
        <div v-if="alcoStep.step" class="block__count">{{
            guestAlco.count + alcoStep.countText
          }}
        </div>
        <div v-if="!alcoStep.step" class="alco">
          <div class="form">
            <div class="counter">
              <div class="counter__panel">
                <img @click="deleteGuest(guestAlco)" src="@/assets/icons/minus.png" alt="">
                <div class="counter__value">{{ guestAlco.count }}</div>
                <img @click="addGuest(guestAlco)" src="@/assets/icons/plus.png" alt="">
              </div>
            </div>
            <div class="form__title">Имена и фамилии гостей</div>
              <div class="form__textarea">
                <textarea v-model="guestAlco.names"
                          placeholder="Например: Иванов Иван и Иванова Наталья"></textarea>
                <img v-if="guestAlco.names" @click="guestAlco.names= ''"
                     src="@/assets/icons/cross.png" alt="">
              </div>
              <button @click="chooseDrinks" class="form__sub"
                      :class="{'form__sub_active': (guestAlco.count && guestAlco.names) || guestAlco.notDrink}">
                {{ dataSending.guestAlco.btnText }}
              </button>
          </div>
          <div class="checkbox">
            <input v-model="guestAlco.notDrink" id="checkbox" type="checkbox">
            <label for="checkbox"></label>
            <div @click="guestAlco.notDrink = !guestAlco.notDrink" class="checkbox__text">Мы не
              употребляем алкоголь
            </div>
          </div>
        </div>
        <div class="block__divider"></div>
        <div v-if="!alcoStep.step" class="block__sub-header block__sub-header_inactive">Шаг 2 —
          Выберите напитки
        </div>
        <div v-if="alcoStep.step === 1" class="select">
          <div class="select__header">
            <div @click="goBack" class="select__back">
              <img src="@/assets/icons/back.png" alt="">
              <div>Вернуться назад</div>
            </div>
            <div class="block__sub-header block__sub-header_grey block__sub-header_m-0">
              {{ alcoStep.text }}
            </div>
          </div>
          <div class="select__content">
            <div v-for="item in alcoArr" :key="item.name" class="select__item">
              <img :src="item.path" alt="">
              <div class="select__name">{{ item.name }}</div>
              <div v-if="!guestAlco.alco[item.name]" @click="setAlco(item, guestAlco.alco)"
                   class="select__btn"
                   :class="{'select__btn_inactive': guestAlco.count === guestAlco.alco.general}">
                <div>Выбрать</div>
                <img src="@/assets/icons/plus_light.png" alt="">
              </div>
              <div v-else class="select__btn select__btn_selected">
                <img @click="removeAlco(item, guestAlco.alco)" src="@/assets/icons/minus.png"
                     alt="">
                <div>{{ guestAlco.alco[item.name] }}</div>
                <img @click="setAlco(item, guestAlco.alco)" src="@/assets/icons/plus.png" alt="">
              </div>
            </div>
          </div>
          <button @click="sendAlcoInfo" class="select__sub"
                  :class="{'select__sub_active': guestAlco.count === guestAlco.alco.general}">
            Отправить
          </button>
        </div>
        <div v-if="alcoStep.step === 2" class="success">
          <div class="block__sub-header block__sub-header_inactive">{{ alcoStep.text }}</div>
          <div class="success__info">Информация успешно отправлена</div>
        </div>
      </div>
      <div class="block">
        <div class="block__header">Станьте частью праздника</div>
        <div class="block__content">
          <div class="block__half block__half_margin">
            <div class="block__text block__text_margin">
              Будем счастливы, если на нашем празднике прозвучит душевная песня или засияет чувственный танец в вашем исполнении. Предложите свой творческий номер и подарите всем незабываемые эмоции
            </div>
            <div class="block__logo-contact">
              <img src="@/assets/icons/logo_contact.png" alt="">
            </div>
          </div>
          <div class="block__half">
            <div class="form">
              <div class="form__title">Имена и фамилии гостей</div>
                <div class="form__textarea">
                  <img v-if="guestPerform.names" @click="guestPerform.names= ''"
                       src="@/assets/icons/cross.png" alt="">
                  <textarea v-model="guestPerform.names"
                            placeholder="Например: Иванов Иван и Иванова Наталья"></textarea>
                </div>
              <div class="contact-input">
                <div class="contact-input__title"></div>
                <input maxlength="18" v-model="guestPerform.number"  @input="formatPhoneNumber"
                   @keydown="preventDeletePlusSeven" placeholder="+7" type="tel">
              </div>
              <div class="form__title">Описание номера</div>
              <div class="form__textarea">
                <img v-if="guestPerform.desc" @click="guestPerform.desc= ''"
                     src="@/assets/icons/cross.png" alt="">
                <textarea v-model="guestPerform.desc"
                          placeholder="Коротко расскажите, что вы хотите исполнять (песня, танец, сценка и т. д.)"></textarea>
              </div>
                <button class="form__sub"
                        :class="{'form__sub_active': guestPerform.number && guestPerform.names && guestPerform.desc}">
                  {{ dataSending.guestCome.btnText }}
                </button>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="footer">
      <div class="container">
        <div class="footer__title">
          Пожалуйста сообщите о своем прибытии на свадьбу в срок до 05 октября
        </div>
        <div class="footer__date">
          <div class="footer__text">До торжества осталось</div>
          <div class="timer">
            <div class="timer__item">
              <div class="timer__value">{{ days }}</div>
              <div class="timer__label">дней</div>
            </div>
            <div class="timer__divider"></div>
            <div class="timer__item">
              <div class="timer__value">{{ hours }}</div>
              <div class="timer__label">часов</div>
            </div>
            <div class="timer__divider"></div>
            <div class="timer__item">
              <div class="timer__value">{{ minutes }}</div>
              <div class="timer__label">минут</div>
            </div>
            <div class="timer__divider"></div>
            <div class="timer__item">
              <div class="timer__value">{{ seconds }}</div>
              <div class="timer__label">секунд</div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import {ref, reactive, watch, onMounted, onBeforeUnmount} from "vue";

const dataSending = reactive({
  guestCome: {
    btnText: 'Отправить',
    dataIsSend: false,
  },
  guestAlco: {
    btnText: 'Выбрать напитки',
    dataIsSend: false,
  }
})

const guestPerform = reactive({
  names: '',
  number: '+7 ',
  desc: '',
})

const guestCome = reactive({
  names: '',
  count: 0,
})

const guestAlco = reactive({
  names: '',
  count: 0,
  alco: {
    general: 0,
  },
  notDrink: false,
})

let alcoStep = reactive({
  step: 0,
  text: '',
  countText: '',
})

const formatPhoneNumber = (e) => {
  const input = e.target;
  let value = input.value.replace(/\D/g, ''); // Удаляем всё, кроме цифр

  // Если номер не начинается с 7, добавляем её (код России)
  if (!value.startsWith('7') && value.length > 0) {
    value = '7' + value;
  }

  // Ограничиваем длину (10 цифр после 7)
  value = value.substring(0, 11);

  // Форматируем номер
  let formattedValue = '+7 ';
  if (value.length > 1) {
    const rest = value.substring(1);
    formattedValue += rest.length > 0 ? `(${rest.substring(0, 3)}` : '';
    formattedValue += rest.length > 3 ? `) ${rest.substring(3, 6)}` : '';
    formattedValue += rest.length > 6 ? `-${rest.substring(6, 8)}` : '';
    formattedValue += rest.length > 8 ? `-${rest.substring(8, 10)}` : '';
  }

  input.value = formattedValue;
  guestPerform.number = formattedValue;
};

// Запрещаем удалять +7
const preventDeletePlusSeven = (e) => {
  if (e.target.selectionStart <= 3 && (e.key === 'Backspace' || e.key === 'Delete')) {
    e.preventDefault();
  }
};


const chooseDrinks = () => {
  if ((guestAlco.count && guestAlco.names) || guestAlco.notDrink) {
    alcoStep.step = 1
  }
}

const setAlco = (item, obj) => {
  if (guestAlco.count !== obj.general) {
    item.name in obj ? obj[item.name]++ : obj[item.name] = 1
    obj.general++
  }
}

const removeAlco = (item, obj) => {
  if (obj[item.name]) {
    obj[item.name]--
    obj.general--
  }
}

const sendAlcoInfo = () => {
  if (guestAlco.count === guestAlco.alco.general) {
    alcoStep.step = 2
  }
}

const goBack = () => {
  alcoStep.step = 0
  alcoStep.text = 'Шаг 2 — Выберите напитки'
}

const getImageUrl = (imageName) => {
  return new URL(`../assets/img/${imageName}`, import.meta.url).href
}

const alcoArr = [
  { name: 'Шампанское брют', path: getImageUrl('champagne.jpg') },
  { name: 'Вино белое сухое', path: getImageUrl('vino_white.jpg') },
  { name: 'Вино красное сухое', path: getImageUrl('vino_red.jpg') },
  { name: 'Водка «Чистые росы»', path: getImageUrl('vodka.jpg') },
  { name: 'Виски Tenjaku product of Japan', path: getImageUrl('whiskey.jpg') },
  { name: 'Коньяк «Ной Араспел» 5 лет', path: getImageUrl('cognac.jpg') },
]

const addGuest = (obj) => obj.count++
const deleteGuest = (obj) => {
  if (obj.count > 0) {
    obj.count--
  }
}

// Реактивные переменные
const days = ref(0)
const hours = ref(0)
const minutes = ref(0)
const seconds = ref(0)

// Конечная дата - 25 октября 2025
const endDate = new Date("2025-10-25T00:00:00")
let intervalId = null

// Функция обновления таймера
const updateTimer = () => {
  const now = new Date()
  const diff = endDate - now

  if (diff <= 0) {
    days.value = 0
    hours.value = 0
    minutes.value = 0
    seconds.value = 0
    clearInterval(intervalId)
    return
  }

  // Конвертация миллисекунд в дни, часы, минуты, секунды
  const totalSeconds = Math.floor(diff / 1000)
  days.value = Math.floor(totalSeconds / 86400)
  hours.value = Math.floor((totalSeconds % 86400) / 3600)
  minutes.value = Math.floor((totalSeconds % 3600) / 60)
  seconds.value = totalSeconds % 60
}

// Запуск таймера при монтировании компонента
onMounted(() => {
  updateTimer() // Первое обновление сразу
  intervalId = setInterval(updateTimer, 1000)
})

// Очистка таймера при размонтировании компонента
onBeforeUnmount(() => {
  if (intervalId) {
    clearInterval(intervalId)
  }
})

watch(
  () => guestAlco.notDrink,
  (newValue) => {
    dataSending.guestAlco.btnText = newValue
      ? 'Отправить'
      : 'Выбрать напитки'
  }
)

watch(
  () => guestAlco.count,
  (newValue) => {
    if (newValue === 1) {
      alcoStep.text = `Шаг 2 — Выберите 1 напиток`
    }
    if (newValue > 1 && newValue < 5) {
      alcoStep.text = `Шаг 2 — Выберите ${guestAlco.count} напитка`
    }
    if (newValue >= 5) {
      alcoStep.text = `Шаг 2 — Выберите ${guestAlco.count} напитков`
    }
    if (newValue === 1 || newValue >= 5) {
      alcoStep.countText = ' человек'
    } else {
      alcoStep.countText = ' человека'
    }
  }
)

</script>

<style lang="scss" scoped>

.container {
  max-width: 1168px;
  width: 100%;
  margin: 0 auto;
}

.timer {
  display: flex;
  justify-content: center;
  font-family: "TT Hoves Pro";
  color: #fff;
  &__item {
    display: flex;
    align-items: center;
    flex-direction: column;
  }
  &__value {
    font-size: 44px;
    font-weight: 500;
  }
  &__label {
    font-size: 24px;
    line-height: 28px;
    font-weight: 400;
  }
  &__divider {
    height: inherit;
    width: 1px;
    background-color: #CBCBCB;
    margin: 0 16px;
  }
}

.footer {
  width: 100%;
  height: 654px;
  border-top-left-radius: 32px;
  border-top-right-radius: 32px;
  background-color: #A4B494;
  padding-top: 116px;
  padding-bottom: 152px;
  &__title {
    font-family: "TT Hoves Pro";
    font-size: 52px;
    line-height: 56px;
    font-weight: 500;
    text-align: center;
    color: #fff;
    margin-bottom: 100px;
  }
  &__text {
    font-family: "Forum";
    text-align: center;
    font-size: 52px;
    line-height: 54px;
    color: #fff;
    margin-bottom: 40px;
  }
}

.contact-input {
  font-family: "TT Hoves Pro";
  width: 100%;
  input {
    border: 1px solid #8A8D93;
    border-radius: 16px;
    padding: 12px 16px;
    font-size: 18px;
    line-height: 24px;
    width: 100%;
    &:focus {
      border-color: #000;
    }
    &::-webkit-inner-spin-button,
    ::-webkit-outer-spin-button {
      -webkit-appearance: none;
      margin: 0;
    }
  }
}

.success {
  &__info {
    font-family: "TT Hoves Pro";
    font-size: 20px;
    line-height: 24px;
    font-weight: 500;
    max-width: 404px;
    width: 100%;
    padding: 20px 40px;
    background-color: #1CCB01;
    justify-content: center;
    align-items: center;
    margin: 0 auto;
    border-radius: 20px;
    color: #fff;
  }
}

.select {
  &__sub {
    margin: 0 auto;
    border-radius: 20px;
    background-color: #C4C5C8;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 20px 40px;
    font-size: 20px;
    font-weight: 500;
    line-height: 24px;
    color: #fff;
    font-family: 'TT Hoves Pro';
    transition: background-color 0.2s;
    &_active {
      background-color: #000;
      &:hover {
        background-color: #585B5F;
      }
      &:active {
        background-color: #76797F;
      }
    }
  }
  &__header {
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
    margin-bottom: 24px;
  }
  &__back {
    display: flex;
    align-items: center;
    position: absolute;
    left: 0;
    top: 50%;
    transform: translateY(-50%);
    cursor: pointer;
  }
  &__content {
    display: flex;
    margin-bottom: 44px;
  }
  &__item {
    display: flex;
    flex-direction: column;
    flex: 1;
    margin-right: 32px;
    &:last-child {
      margin-right: 0;
    }
  }
  &__name {
    text-align: start;
    word-break: break-word;
    font-family: "TT Hoves Pro";
    font-size: 22px;
    line-height: 24px;
    font-weight: 400;
    color: #474747;
    margin-top: 8px;
    margin-bottom: 16px;
  }
  &__btn {
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 16px;
    font-family: 'TT Hoves Pro';
    transition: background-color 0.2s;
    background-color: #000;
    color: #fff;
    height: 44px;
    cursor: pointer;
    user-select: none;
    font-size: 16px;
    line-height: 20px;
    font-weight: 500;
    &:hover {
      background-color: #585B5F;
    }
    img {
      margin-left: 8px;
    }
    &_inactive {
      background-color: #C4C5C8;
      &:hover {
        background-color: #C4C5C8;
      }
    }
    &_selected {
      position: relative;
      background-color: #fff;
      color: #000;
      box-shadow: 0 2px 8px rgba(0, 0, 0, 0.06), 2px 0 8px rgba(0, 0, 0, 0.06);
      cursor: auto;
      font-size: 22px;
      line-height: 24px;
      img {
        margin-left: 0;
        cursor: pointer;
        position: absolute;
        top: 50%;
        transform: translateY(-50%);
        &:first-child {
          left: 16px;
        }
        &:last-child {
          right: 16px;
        }
      }
      &:hover {
        background-color: #fff;
      }
    }
  }
}

.checkbox {
  display: flex;
  margin-top: 24px;
  &__text {
    font-family: "TT Hoves Pro";
    font-size: 16px;
    line-height: 20px;
    cursor: pointer;
  }
  input {
    visibility: hidden;
    position: absolute;
    &:checked + label:after {
      content: '';
      background: url('@/assets/icons/checkbox.png') no-repeat center;
      width: 20px;
      height: 20px;
      left: 0;
      top: 0;
      opacity: 1;
    }
  }
  label {
    position: relative;
    padding-left: 32px;
    cursor: pointer;
    &::before {
      content: '';
      position: absolute;
      left: 0;
      top: 0;
      width: 20px;
      height: 20px;
      border: 1px solid #C8CCD0;
      border-radius: 4px;
      background: #fff;
    }
    &::after {
      content: '';
      position: absolute;
      left: 0;
      top: 0;
      opacity: 0;
      transition: opacity 0.2s;
    }
  }
}

.alco {
  max-width: 458px;
  width: 100%;
  margin: 36px auto 0;
}

.palitra {
  font-family: "TT Hoves Pro";
  display: flex;
  height: 400px;
  &__item {
    padding: 20px 16px;
    color: #fff;
    font-size: 22px;
    font-weight: 600;
    display: flex;
    align-items: flex-end;
    border-radius: 16px;
    margin-right: 8px;
    flex: 1;
    &:nth-child(1) {
      background-color: #A4B494;
    }
    &:nth-child(2) {
      background-color: #DB8C6C;
    }
    &:nth-child(3) {
      background-color: #94795D;
    }
    &:nth-child(4) {
      background-color: #3B322D;
    }
    &:nth-child(5) {
      background-color: #EEE2D0;
      color: #000;
      margin-right: 0;
    }
  }
}

.divider {
  position: relative;
  padding: 42px 0;
  &__line {
    position: absolute;
    height: 100%;
    width: 2px;
    background-color: #CBCBCB;
    left: 50%;
    top: 0;
    transform: translateX(-50%);
    &::after {
      content: '';
      position: absolute;
      top: 0;
      left: 50%;
      transform: translateX(-50%);
      width: 10px;
      height: 10px;
      border-radius: 50%;
      background-color: #CBCBCB;
    }
    &::before {
      content: '';
      position: absolute;
      bottom: 0;
      left: 50%;
      transform: translateX(-50%);
      width: 10px;
      height: 10px;
      border-radius: 50%;
      background-color: #CBCBCB;
    }
  }
}

.timing {
  font-family: "TT Hoves Pro";
  font-weight: 400;
  display: flex;
  align-items: center;
  justify-content: space-between;
  &__item {
    flex-grow: 1;
  }
  &__time {
    font-size: 36px;
    line-height: 40px;
    text-align: center;
  }
  &__event {
    font-size: 24px;
    line-height: 28px;
    color: #666666;
    text-align: center;
  }
  &__line {
    display: flex;
    align-items: center;
    margin: 4px 0 4px 16px;
    &_reverse {
      flex-direction: row-reverse;
      margin-right: 16px;
      margin-left: 0;
    }
    div {
      &:first-child {
        width: 5px;
        height: 5px;
        border-radius: 50%;
        background-color: #CBCBCB;
      }
      &:last-child {
        width: 100%;
        height: 1px;
        background-color: #CBCBCB;
      }
    }
  }
}

.intro {
  background: url("@/assets/img/main_banner.jpg") no-repeat center;
  background-size: cover;
  height: 100dvh;
  width: 100%;
  margin-bottom: 72px;
  &__header {
    font-family: "TT Hoves Pro";
    font-weight: 500;
    font-size: 18px;
    color: #fff;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding-top: 10px;
    line-height: 24px;
    margin-bottom: 145px;
    span {
      cursor: pointer;
      &:nth-child(2) {
        margin: 0 32px;
      }
    }
  }
  &__logo {
    width: 80px;
    height: 60px;
    img {
      width: 100%;
      height: 100%;
    }
  }
  &__date {
    font-family: "TT Hoves Pro";
    font-size: 52px;
    line-height: 56px;
    color: #fff;
    text-align: center;
    margin-bottom: 32px;
  }
  &__title {
    color: #fff;
    text-align: center;
    font-family: "Forum";
    div {
      &:first-child {
        font-size: 112px;
        margin-bottom: 20px;
      }
      &:last-child {
        font-size: 64px;
      }
    }
  }
}

.invite {
  font-family: "TT Hoves Pro";
  font-size: 34px;
  font-weight: 400;
  line-height: 40px;
  margin-bottom: 8px;
}

.block {
  margin-bottom: 116px;
  &__logo-contact {
    height: 362px;
    background-color: #EEE2D0;
    display: flex;
    justify-content: center;
    align-items: center;
    border-radius: 16px;
  }
  &__content {
    display: flex;
    align-items: center;
    &_margin {
      margin-bottom: 80px;
    }
    &_margin-s {
      margin-bottom: 24px;
    }
  }
  &__sub-header {
    font-family: "TT Hoves Pro";
    font-weight: 500;
    text-align: center;
    font-size: 32px;
    line-height: 36px;
    margin-bottom: 24px;
    &_grey {
      color: #474747;
    }
    &_inactive {
      color: #A4A4A4;
    }
    &_m-0 {
      margin-bottom: 0;
    }
  }
  &__count {
    font-family: "TT Hoves Pro";
    text-align: center;
    font-size: 32px;
    line-height: 26px;
    font-weight: 500;
    color: #1CCB01;
  }
  &__half {
    width: 50%;
    &_margin {
      margin-right: 72px;
    }
    &_logo {
      height: 462px;
      background-color: #6D8A61;
      display: flex;
      justify-content: center;
      align-items: center;
      border-radius: 16px;
    }
  }
  &__header {
    font-family: "Forum";
    font-size: 52px;
    line-height: 54px;
    margin-bottom: 40px;
    text-align: center;
  }
  &__title {
    font-family: "TT Hoves Pro";
    font-size: 24px;
    font-weight: 500;
    margin-bottom: 12px;
  }
  &__text {
    font-family: "TT Hoves Pro";
    font-size: 20px;
    font-weight: 400;
    line-height: 24px;
    &_palitra {
      font-size: 24px;
      line-height: 28px;
    }
    &_margin {
      margin-bottom: 24px;
    }
  }
  &__divider {
    width: 100%;
    height: 1px;
    background-color: #CBCBCB;
    margin: 40px 0;
  }
}

.names {
  display: flex;
  justify-content: space-between;
  font-size: 24px;
  line-height: 28px;
  font-family: "Forum";
  margin: 8px 0 36px 0;
}

.desc {
  font-family: "TT Hoves Pro";
  font-weight: 500;
  font-size: 18px;
  line-height: 20px;
}

.form {
  &__textarea {
    position: relative;
  }
  textarea {
    min-height: 125px;
    border: 1px solid #DBDBDB;
    border-radius: 16px;
    padding: 12px 16px;
    resize: none;
    margin-bottom: 8px;
    width: 100%;
    font-size: 18px;
    line-height: 24px;
    font-family: 'TT Hoves Pro';
    &::placeholder {
      color: #000;
    }
    &:focus {
      border-color: #000;
    }
  }
  img {
    top: 8px;
    right: 8px;
    position: absolute;
    width: 20px;
    height: 20px;
    cursor: pointer;
  }
  &__title {
    font-family: 'TT Hoves Pro';
    font-size: 16px;
    line-height: 20px;
    font-weight: 400;
    margin: 12px 0 4px 0;
  }
  &__sub {
    height: 64px;
    border-radius: 20px;
    background-color: #C4C5C8;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
    font-size: 20px;
    font-weight: 500;
    line-height: 24px;
    color: #fff;
    font-family: 'TT Hoves Pro';
    transition: background-color 0.2s;
    &_active {
      background-color: #000;
      &:hover {
        background-color: #585B5F;
      }
      &:active {
        background-color: #76797F;
      }
    }
  }
}

.counter {
  font-family: "TT Hoves Pro";
  margin-bottom: 23px;
  &__title {
    font-size: 16px;
    line-height: 20px;
    font-weight: 400;
    margin-bottom: 4px;
  }
  &__panel {
    display: flex;
    max-width: 208px;
    width: 100%;
    justify-content: center;
    align-items: center;
    padding: 16px 20px;
    border-radius: 16px;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.06), 2px 0 8px rgba(0, 0, 0, 0.06);
    position: relative;
    user-select: none;
    img {
      cursor: pointer;
      position: absolute;
      top: 50%;
      transform: translateY(-50%);
      &:first-child {
        left: 20px
      }
      &:last-child {
        right: 20px;
      }
    }
  }
  &__value {
    font-size: 28px;
    line-height: 32px;
    font-weight: 500;
  }
}
</style>
