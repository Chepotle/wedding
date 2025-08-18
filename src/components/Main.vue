<template>
  <div class="wedding">
    <div class="intro">
      <div class="burger" :class="burger ? 'burger__open' : 'burger__close'">
        <div v-if="burger" class="burger__content">
          <a @click="goAnchor" href="#invite">Приглашение</a>
          <a @click="goAnchor" href="#timing">Тайминг</a>
          <a @click="goAnchor" href="#location">Локация</a>
          <a @click="goAnchor" href="#dress">Дресс-код</a>
          <a @click="goAnchor" href="#drinks">Напитки</a>
          <a @click="goAnchor" href="#art">Творчество</a>
          <div class="burger__date">25 октября 2025</div>
          <div class="burger__names">Артур и Аннелия</div>
        </div>
      </div>
      <div class="container">
        <div class="intro__header">
          <div class="intro__menu">
            <a href="#invite">Приглашение</a>
            <a href="#timing">Тайминг</a>
            <a href="#location">Локация</a>
          </div>
          <div class="intro__logo">
            <img src="@/assets/icons/logo_intro.png" alt="">
          </div>
          <div class="intro__menu">
            <a href="#dress">Дресс-код</a>
            <a href="#drinks">Напитки</a>
            <a href="#art">Творчество</a>
          </div>
          <img @click="burger = !burger" v-if="!burger" src="@/assets/icons/burger.png" alt="" class="burger__icon">
          <img @click="burger = !burger" v-else src="@/assets/icons/close.png" alt="" class="burger__icon">
        </div>
        <div class="intro__date">25 октября 2025</div>
        <div class="intro__title">
          <div>Артур и Аннелия</div>
          <div>Свадебное торжество</div>
        </div>
      </div>
    </div>
    <div class="container">
      <div id="invite" class="block">
        <div class="block__content block__content_reverse">
          <div class="block__half block__half_margin">
            <img src="@/assets/img/flowers.jpg" alt="">
            <div v-if="!dataSending.guestCome.dataIsSend" class="form form_mob">
              <div class="desc">
                Напишите, пожалуйста, в каком составе вы прибудете на торжество, укажите имя и
                фамилию,
                имена членов вашей семьи
              </div>
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
              <button @click="sendGuestCome" class="form__sub"
                      :class="{'form__sub_active': guestCome.count && guestCome.names}">
                {{ dataSending.guestCome.btnText }}
              </button>
            </div>
            <div v-if="dataSending.guestCome.dataIsSend" class="success success_mob">
              <div class="success__text">Спасибо за информацию!</div>
              <div class="success__info success__info_left">Данные успешно отправлены</div>
            </div>
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
            <div v-if="dataSending.guestCome.dataIsSend" class="success success_desc">
              <div class="success__text">Спасибо за информацию!</div>
              <div class="success__info success__info_left">Данные успешно отправлены</div>
            </div>

            <div v-if="!dataSending.guestCome.dataIsSend" class="form form_desc">
              <div class="desc">
                Напишите, пожалуйста, в каком составе вы прибудете на торжество, укажите имя и
                фамилию,
                имена членов вашей семьи
              </div>
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
                <button @click="sendGuestCome" class="form__sub"
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
        <div class="block__content block__content_reverse">
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
          <div class="block__half block__half_margin-s-mob">
            <img src="@/assets/img/vostok.jpg" alt="">
          </div>
        </div>
      </div>
      <div id="timing" class="block">
        <div class="block__header">Тайминг</div>
        <div class="block__sub-header block__sub-header_grey">25 октября 2025</div>
        <div class="divider">
          <div class="divider__line"></div>
          <div class="block__content block__content_margin-s">
            <div class="block__half block__half_timing">
              <div class="timing timing_reverse">
                <picture>
                  <source srcset="@/assets/icons/13.png" media="(min-width: 1439px)">
                  <source srcset="@/assets/icons/mobile/13.png" media="(min-width: 0)">
                  <img src="@/assets/icons/mobile/13.png" alt="">
                </picture>
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
            <div class="block__half block__half_timing">
              <div class="timing">
                <div class="timing__item">
                  <div class="timing__time">14:00</div>
                  <div class="timing__line timing__line_reverse">
                    <div></div>
                    <div></div>
                  </div>
                  <div class="timing__event">национальный обряд «Беташар»</div>
                </div>
                <picture>
                  <source srcset="@/assets/icons/14.png" media="(min-width: 1439px)">
                  <source srcset="@/assets/icons/mobile/14.png" media="(min-width: 0)">
                  <img src="@/assets/icons/mobile/14.png" alt="">
                </picture>
              </div>
            </div>
          </div>
          <div class="block__content block__content_margin-s">
            <div class="block__half block__half_timing">
              <div class="timing timing_reverse">
                <picture>
                  <source srcset="@/assets/icons/14_20.png" media="(min-width: 1439px)">
                  <source srcset="@/assets/icons/mobile/14_20.png" media="(min-width: 0)">
                  <img src="@/assets/icons/mobile/14_20.png" alt="">
                </picture>
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
            <div class="block__half block__half_timing">
              <div class="timing">
                <div class="timing__item">
                  <div class="timing__time">14:40</div>
                  <div class="timing__line timing__line_reverse">
                    <div></div>
                    <div></div>
                  </div>
                  <div class="timing__event">фотосессия молодоженов <br/> с гостями</div>
                </div>
                <picture>
                  <source srcset="@/assets/icons/14_40.png" media="(min-width: 1439px)">
                  <source srcset="@/assets/icons/mobile/14_40.png" media="(min-width: 0)">
                  <img src="@/assets/icons/mobile/14_40.png" alt="">
                </picture>
              </div>
            </div>
          </div>
          <div class="block__content">
            <div class="block__half block__half_timing">
              <div class="timing timing_reverse">
                <picture>
                  <source srcset="@/assets/icons/15_30.png" media="(min-width: 1439px)">
                  <source srcset="@/assets/icons/mobile/15_30.png" media="(min-width: 0)">
                  <img src="@/assets/icons/mobile/15_30.png" alt="">
                </picture>
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
      <div id="location" class="block">
        <div class="block__header">Локация</div>
        <div class="block__sub-header">«Олимпия» загородный клуб</div>
        <div class="block__content map">
          <div id="map" ref="mapFindOrg" class="map__cont"></div>
          <div class="map__desc">Волгоградская область, Среднеахтубинский район, Краснослободск, посёлок Вторая Пятилетка</div>
          <div class="map__img">
            <img src="@/assets/img/location.jpg" alt="">
          </div>
        </div>
      </div>
      <div id="dress" class="block">
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
      <div id="drinks" class="block">
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
      <div id="art" class="block">
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
                <button @click="sendGuestPerfom" class="form__sub"
                        :class="{'form__sub_active': guestPerform.number && guestPerform.names && guestPerform.desc}">
                  {{ dataSending.guestPerfom.btnText }}
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
import ymaps from 'ymaps';


let burger = ref(false)

const dataSending = reactive({
  guestCome: {
    btnText: 'Отправить',
    dataIsSend: false,
  },
  guestAlco: {
    btnText: 'Выбрать напитки',
    dataIsSend: false,
  },
  guestPerfom: {
    btnText: 'Отправить',
    dataIsSend: false,
  }
})

const goAnchor = () => {
  document.body.style.overflow = ''
  document.body.style.touchAction = ''
  burger = false
}

const sendGuestCome = async () => {
  if (guestCome.count && guestCome.names) {
    try {
      dataSending.guestCome.btnText = 'Отправка';

      let response = await fetch('/action.php', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json;charset=utf-8'
        },
        body: JSON.stringify(guestCome)
      });

      if (!response.ok) {
        throw new Error(`Ошибка HTTP: ${response.status}`);
      } else {
        dataSending.guestCome.dataIsSend = true;
      }

    } catch (error) {
      console.error('Ошибка при отправке:', error);
      // dataSending.guestCome.btnText = 'Ошибка, попробуйте снова';
    }
  }
}

const sendAlcoInfo = async () => {
  if (guestAlco.count === guestAlco.alco.general) {
    try {
      dataSending.guestAlco.btnText = 'Отправка';

      let response = await fetch('/action.php', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json;charset=utf-8'
        },
        body: JSON.stringify(guestAlco)
      });

      if (!response.ok) {
        throw new Error(`Ошибка HTTP: ${response.status}`);
      } else {
        dataSending.guestAlco.dataIsSend = true;
        alcoStep.step = 2
      }

    } catch (error) {
      console.error('Ошибка при отправке:', error);
      // dataSending.guestCome.btnText = 'Ошибка, попробуйте снова';
    }
  }
}

const sendGuestPerfom = async () => {
  if (guestPerform.number && guestPerform.names && guestPerform.desc) {
    try {
      dataSending.guestPerfom.btnText = 'Отправка';

      let response = await fetch('/action.php', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json;charset=utf-8'
        },
        body: JSON.stringify(guestPerform)
      });

      if (!response.ok) {
        throw new Error(`Ошибка HTTP: ${response.status}`);
      } else {
        dataSending.guestPerfom.dataIsSend = true;
      }

    } catch (error) {
      console.error('Ошибка при отправке:', error);
      // dataSending.guestCome.btnText = 'Ошибка, попробуйте снова';
    }
  }
}

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
const Createlayout = (e) => {return e.templateLayoutFactory.createClass(`<div dir="ltr" aria-hidden="true" class="map-placemark__wrapper">
        <div class="search-placemark-view _position_right" data-icon-type="rubric" style="margin-top: -17px; margin-left: -17px;">
        <div class="search-placemark-view__icon" style="width: 60px; height: 68px;"><div class="search-placemark-icon _mode_base _group-mode_default _state_default">
        <div style="position: relative; width: 60px; height: 68px;"><div>
        <svg width="60" height="68" viewBox="0 0 60 68" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"><defs><path d="M23.51 51.523a.5.5 0 0 1-.5.477c-.29 0-.51-.21-.52-.477-.145-3.168-1.756-5.217-4.832-6.147C7.53 42.968 0 33.863 0 23 0 10.297 10.297 0 23 0s23 10.297 23 23c0 10.863-7.53 19.968-17.658 22.376-3.076.93-4.687 2.98-4.83 6.147z" id="ae96eeecd750ec2a83543f00c9bc789d__b"></path><filter x="-21.7%" y="-15.4%" width="143.5%" height="138.5%" filterUnits="objectBoundingBox" id="ae96eeecd750ec2a83543f00c9bc789d__a"><feGaussianBlur in="SourceGraphic" stdDeviation="3"></feGaussianBlur><feOffset dy="2"></feOffset><feComponentTransfer><feFuncA type="linear" slope=".3"></feFuncA></feComponentTransfer></filter></defs><g fill="none" fill-rule="evenodd"><g fill-rule="nonzero" transform="translate(7 5)" fill="currentColor"><use filter="url(#ae96eeecd750ec2a83543f00c9bc789d__a)" xlink:href="#ae96eeecd750ec2a83543f00c9bc789d__b"></use><use xlink:href="#ae96eeecd750ec2a83543f00c9bc789d__b"></use></g><path d="M30 68c-2.21 0-4-1.79-4-4s1.79-4 4-4 4 1.79 4 4-1.79 4-4 4z" fill="#fff" fill-rule="nonzero"></path><path d="M30 66a2 2 0 1 0 .001-3.999A2 2 0 0 0 30 66z" fill="currentColor"></path></g></svg>
        </div><div style="position: absolute; left: 25px; top: 24px;">
        <div class="rubric-placemark-icons-provider__base-content _pin-type_default">
        <svg width="20" height="20" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path d="M9.857 8C8.082 8.02 6.02 7.53 5 6c1.036-1.554 3.144-1.498 4.937-.944C8.53 3.802 7.493 2.03 8 0c.851 0 4.602 1.45 5.698 4.966C15.771 3.78 19.331 3.331 22 6c-1.814 1.814-5.089 2.165-7.396 1.939C16.49 9.059 18 11.029 18 13c-1.759 0-5.452-1.547-6.316-4.642C8.679 10.201 6 13.983 6 22v.2a.8.8 0 0 1-.8.8H2.8a.8.8 0 0 1-.8-.8V22c0-6.5 2.619-11.167 7.857-14z" fill="currentColor"></path><path d="M8.68 23a.4.4 0 0 1-.35-.594l4.376-7.877a.4.4 0 0 1 .665-.051L16.5 18.5l2.206-1.324a.4.4 0 0 1 .513.087l4.234 5.08a.4.4 0 0 1-.307.657H8.68z" fill="currentColor"></path></svg>
        </div></div></div></div></div>
        <div class="search-placemark-view__title">
        <div class="search-placemark-title _background _position_right _no-truncate">
        <div class="search-placemark-title__title"><div class="search-placemark-title__title-text">{{properties.name}}</div>
        <div class="search-placemark-title__title-rating"><span class="search-placemark-title-modular-hint-view">
        <span class="inline-image _loaded icon search-placemark-title-modular-hint-view__rating-image" aria-hidden="true" role="button" tabindex="-1" style="font-size: 0px; line-height: 0;">
        <svg width="12" height="12" viewBox="0 0 12 12" xmlns="http://www.w3.org/2000/svg">
        <path fill-rule="evenodd" clip-rule="evenodd" d="M5.99 9.19l-2.711 1.744c-.304.195-.687-.083-.603-.435l.792-3.323-2.32-1.9c-.279-.229-.14-.685.218-.716l3.018-.262L5.625 1.25a.398.398 0 0 1 .739.001l1.231 3.047 3.04.262c.358.031.496.488.216.717l-2.33 1.9.792 3.324c.084.352-.3.63-.603.435L5.99 9.189z" fill="currentColor">
        </path></svg></span><span class="search-placemark-title-modular-hint-view__rating">{{properties.rating.score}}</span></span></div></div>
        <div class="search-placemark-title__subtitle">
        <span class="search-placemark-title__subtitle-item"><span class="search-placemark-title-modular-hint-view"> База, дом отдыха
        </span></span></div></div> </div></div></div>`,
        {build:function(){this.constructor.superclass.build.call(this)}});
      }
onMounted(() => {
  updateTimer() // Первое обновление сразу
  intervalId = setInterval(updateTimer, 1000)
  const maps = ymaps.load('//api-maps.yandex.ru/2.1/?lang=ru_RU&apikey=48d4964b-4fe1-4b32-8768-43ec07c075de').then((maps)=>{
      const map = new maps.Map('map', {
        center: [48.666096, 44.564278],
        zoom: 14
    });
    maps.findOrganization('1110837623').then((orgGeoObject) =>{
      orgGeoObject.options.set('preset','islands#greyCircleIcon');
      orgGeoObject.options.set("iconLayout",Createlayout(maps));
      orgGeoObject.options.set("iconShape",{type:"Rectangle",coordinates:[[-25,-25],[125,25]]});
      orgGeoObject.options.set("iconOffset",[-0,-0]);
      map.geoObjects.add(orgGeoObject);
    }
    // 1110837623 id org
  ).catch(err => console.log(err));
}).catch(error => console.log('Failed to load Yandex Maps', error));
});
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

watch(burger, (open) => {
  if (open) {
    document.body.style.overflow = 'hidden'
    document.body.style.touchAction = 'none'
    window.scrollTo({
      top: 0,
      behavior: 'smooth'
    })
  } else {
    document.body.style.overflow = ''
    document.body.style.touchAction = ''
  }
})

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

<style lang="scss">
@use "@/assets/scss/media" as *;
@use "src/assets/scss/mapmarker" as *;

.burger {
  position: absolute;
  top: 0;
  left: 0;
  background-color: #000;
  height: 100dvh;
  width: 100%;
  transition: max-height 0.25s ease;
  &__content {
    padding-top: 124px;
    padding-left: 16px;
    display: flex;
    flex-direction: column;
    color: #fff;
    a {
      font-family: "TT Hoves Pro";
      font-size: 22px;
      line-height: 24px;
      font-weight: 500;
      color: #fff;
      margin-bottom: 32px;
    }
  }
  &__names {
    font-family: "Forum";
    font-size: 44px;
  }
  &__date {
    font-family: "TT Hoves Pro";
    font-weight: 500;
    font-size: 24px;
    line-height: 28px;
    margin-top: 148px;
    margin-bottom: 24px;
  }
  &__open {
    max-height: 100%;
  }
  &__close {
    max-height: 0;
  }
  &__icon {
    position: absolute;
    right: 16px;
    top: 20px;
  }
}


#map{
  width:100%;
  height: 100%;
  min-width: 100px;
  min-height: 100px;
}
.container {
  max-width: 1168px;
  width: 100%;
  margin: 0 auto;
  padding: 0 16px;
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
    @include media("max", "m") {
      font-size: 36px;
      line-height: 40px;
    }
  }
  &__label {
    font-size: 24px;
    line-height: 28px;
    font-weight: 400;
    @include media("max", "m") {
      font-size: 20px;
      line-height: 24px;
    }
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
  @include media("max", "m") {
    padding-top: 72px;
    padding-bottom: 132px;
    height: 540px;
  }
  &__title {
    font-family: "TT Hoves Pro";
    font-size: 52px;
    line-height: 56px;
    font-weight: 500;
    text-align: center;
    color: #fff;
    margin-bottom: 100px;
    @include media("max", "m") {
      font-weight: 400;
      font-size: 32px;
      line-height: 36px;
      margin-bottom: 60px;
      text-align: left;
    }
  }
  &__text {
    font-family: "Forum";
    text-align: center;
    font-size: 52px;
    line-height: 54px;
    color: #fff;
    margin-bottom: 40px;
    @include media("max", "m") {
      margin-bottom: 24px;
      font-size: 34px;
      line-height: 36px;
    }
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
  &_desc {
    @include media("max", "m") {
      display: none;
    }
  }
  &_mob {
    display: none;
    @include media("max", "m") {
      display: block;
    }
  }
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
    &_left {
      max-width: 100%;
    }
  }
  &__text {
    font-size: 18px;
    line-height: 20px;
    font-family: "TT Hoves Pro";
    font-weight: 500;
    margin-bottom: 36px;
    margin-top: 24px;
    @include media("max", "m") {

    }
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
    @include media("max", "m") {
      flex-direction: column;
      align-items: flex-start;
    }
  }
  &__back {
    display: flex;
    align-items: center;
    position: absolute;
    left: 0;
    top: 50%;
    transform: translateY(-50%);
    cursor: pointer;
    color: #2688EB;
    @include media("max", "m") {
      position: static;
      justify-content: flex-start;
      transform: translateY(0);
      margin-bottom: 16px;
    }
  }
  &__content {
    display: flex;
    margin-bottom: 44px;
    row-gap: 12px;
    justify-content: center;
    column-gap: 32px;
    @include media("max", "m") {
      flex-wrap: wrap;
      column-gap: 12px;
    }
  }
  &__item {
    display: flex;
    flex-direction: column;
    max-width: 168px;
    width: 100%;
    @include media("max", "m") {
      max-width: 165px;
    }
    img {
      &:first-child {
        max-width: 100%;
        overflow: hidden;
      }
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
    margin-top: auto;
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
  @include media("max", "m") {
    max-width: 100%;
  }
}

.palitra {
  font-family: "TT Hoves Pro";
  display: flex;
  height: 400px;
  gap: 8px;
  @include media("max", "m") {
    flex-wrap: wrap;
    height: 472px;
  }
  &__item {
    padding: 20px 16px;
    color: #fff;
    font-size: 22px;
    font-weight: 600;
    display: flex;
    align-items: flex-end;
    border-radius: 16px;
    flex: 1;
    @include media("max", "m") {
      padding: 12px;
      font-size: 18px;
      line-height: 22px;
    }
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
    @include media("max", "m") {
      left: 0;
      transform: translateX(0);
    }
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
  @include media("max", "m") {
    flex-grow: 1;

  }
  &_reverse {
    @include media("max", "m") {
      flex-direction: row-reverse;
    }
  }
  &__item {
    flex-grow: 1;
  }
  &__time {
    font-size: 36px;
    line-height: 40px;
    text-align: center;
    @include media("max", "m") {
      text-align: left;
      margin-left: 8px;
      font-size: 24px;
      line-height: 28px;
    }
  }
  &__event {
    font-size: 24px;
    line-height: 28px;
    color: #666666;
    text-align: center;
    @include media("max", "m") {
      text-align: left;
      margin-left: 8px;
      font-size: 16px;
      line-height: 20px;
    }
  }
  &__line {
    display: flex;
    align-items: center;
    margin: 4px 0 4px 16px;
    @include media("max", "m") {
      flex-direction: row-reverse;
      margin-right: 7px;
      margin-left: 0;
    }
    &_reverse {
      flex-direction: row-reverse;
      margin-right: 16px;
      margin-left: 0;
      @include media("max", "m") {
        margin-right: 7px;
      }
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
  border-bottom-left-radius: 24px;
  border-bottom-right-radius: 24px;
  @include media("max", "m") {
    margin-bottom: 40px;
  }
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
    position: relative;
    z-index: 10;
    @include media("max", "m") {
      justify-content: center;
      margin-bottom: 164px;
    }
    a {
      color: #fff;
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
    @include media("max", "m") {
      font-size: 24px;
      line-height: 28px;
      margin-bottom: 24px;
    }
  }
  &__title {
    color: #fff;
    text-align: center;
    font-family: "Forum";
    div {
      &:first-child {
        font-size: 112px;
        margin-bottom: 20px;
        @include media("max", "m") {
          font-size: 48px;
          margin-bottom: 12px;
        }
      }
      &:last-child {
        font-size: 64px;
        @include media("max", "m") {
          font-size: 32px;
          line-height: 36px;
        }
      }
    }
  }
  &__menu {
    @include media("max", "m") {
      display: none;
    }
  }
}

.invite {
  font-family: "TT Hoves Pro";
  font-size: 34px;
  font-weight: 400;
  line-height: 40px;
  margin-bottom: 8px;
  @include media("max", "m") {
    font-size: 32px;
    line-height: 36px;
  }
}

.block {
  margin-bottom: 116px;
  @include media("max", "m") {
    margin-bottom: 72px;
  }
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
    @include media("max", "m") {
      flex-direction: column;
    }
    &_reverse {
      @include media("max", "m") {
        flex-direction: column-reverse;
      }
    }
    &_margin {
      margin-bottom: 80px;
      @include media("max", "m") {
        margin-bottom: 24px;
      }
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
    @include media("max", "m") {
      font-size: 22px;
      line-height: 26px;
      margin-bottom: 16px;
      text-align: left;
    }
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
    @include media("max", "m") {
      display: flex;
      flex-direction: column;
      width: 100%;
    }
    &_timing {
      @include media("max", "m") {
        flex-direction: row;
      }
    }

    img {
      max-width: 100%;
      overflow: hidden;
    }
    &_margin {
      margin-right: 72px;
      @include media("max", "m") {
        margin-right: 0;
      }
    }
    &_margin-s-mob {
      @include media("max", "m") {
        margin-bottom: 24px;
      }
    }
    &_logo {
      height: 462px;
      background-color: #6D8A61;
      display: flex;
      justify-content: center;
      align-items: center;
      border-radius: 16px;
      @include media("max", "m") {
        height: auto;
        padding: 57px;
        margin-bottom: 24px;
      }
    }
  }
  &__header {
    font-family: "Forum";
    font-size: 52px;
    line-height: 54px;
    margin-bottom: 40px;
    text-align: center;
    @include media("max", "m") {
      margin-bottom: 20px;
      font-size: 36px;
      line-height: 40px;
      text-align: left;
    }
  }
  &__title {
    font-family: "TT Hoves Pro";
    font-size: 24px;
    font-weight: 500;
    margin-bottom: 12px;
    @include media("max", "m") {
      font-size: 20px;
    }
  }
  &__text {
    font-family: "TT Hoves Pro";
    font-size: 20px;
    font-weight: 400;
    line-height: 24px;
    @include media("max", "m") {
      font-size: 18px;
      line-height: 22px;

    }
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
    @include media("max", "m") {
      margin: 28px 0;
    }
  }
}

.names {
  display: flex;
  justify-content: space-between;
  font-size: 24px;
  line-height: 28px;
  font-family: "Forum";
  margin: 8px 0 36px 0;
  @include media("max", "m") {
    margin-bottom: 24px;
  }
}

.desc {
  font-family: "TT Hoves Pro";
  font-weight: 500;
  font-size: 18px;
  line-height: 20px;
  @include media("max", "m") {
    font-size: 16px;
  }
}

.form {
  &_mob {
    display: none;
    @include media("max", "m") {
      margin-top: 24px;
      display: block;
    }
  }
  &_desc {
    @include media("max", "m") {
      display: none;
    }
  }
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
    @include media("max", "m") {
      font-size: 16px;
      line-height: 20px;
    }
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
    @include media("max", "m") {
      font-size: 14px;
      line-height: 16px;
    }
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
  @include media("max", "m") {
    margin-bottom: 36px;
  }
  &__title {
    font-size: 16px;
    line-height: 20px;
    font-weight: 400;
    margin-bottom: 4px;
    @include media("max", "m") {
      font-size: 14px;
      line-height: 16px;
    }
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
br {
  @include media("max", "m") {
    display: none;
  }
}
.map{
  display: grid;
  grid-template-columns: 1fr 442px;
  grid-template-rows: 1fr auto;
  column-gap: 24px;
  row-gap: 8px;
  grid-template-areas: 'm i' 'd i';
  @include media("max", "m") {
    grid-template-columns: 1fr;
    grid-template-areas: 'm' 'd' 'i';
    grid-template-rows: 225px auto auto;
  }
  &__cont{
    grid-area: m;
    border-radius: 16px;
    overflow: hidden;
  }
  &__desc{
    grid-area: d;
  }
  &__img{
    border-radius: 16px;
    grid-area: i;
    img {
      max-width: 100%;
      overflow: hidden;
    }
    @include media("max", "m") {
      display: flex;
      flex-direction: column;
    }
  }
}


</style>
