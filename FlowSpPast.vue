<template>
  <div :class="$style.SpPast">
    <h4 :class="['mb-2', $style.Heading]">
      <span :class="大きくするstyle">発症前<strong>2</strong>週間以内</span>
      <span>の出来ごとと症状</span>
    </h4>
    <p class="mb-5">
      <span :class="$style.small">「新型コロナウイルス感染者」と</span><br />
      <span :class="$style.underline">濃厚接触</span>をした方<br />
    </p>
    <div :class="['mb-4', $style.flexContainer]">
      <div :class="$style.item">
        <div>
          {{ $t('発熱') }}
        </div>
      </div>
      <div :class="$style.item">
        {{ $t('または') }}
      </div>
      <div :class="$style.item">
        <div>
          {{ $t('呼吸器症状') }}
        </div>
      </div>
    </div>
    <div :class="['mb-5', $style.hr]" />
    <p class="mb-5">
      <span :class="$style.small">流行地域への渡航・居住歴がある方</span><br />
      <span :class="$style.underline">ご本人</span>か<!--
   --><span :class="$style.underline">濃厚接触</span>をした方
    </p>
    <div :class="['mb-4', $style.flexContainer]">
      <div :class="$style.item">
        <div>
          {{ $t('呼吸器症状') }}
        </div>
      </div>
      <div :class="$style.item">
        {{ $t('かつ') }}
　　　<div :class="$style.item">
      <div>
      <small>発熱</small>
      <span><span>37.5℃</span>以上</span>
      </div>
      </div>
    </div>
    <a
      v-scroll-to="'#consult'"
      href="#consult"
      :class="['pa-5', $style.counter]"
    >
      {{ $t('新型コロナ受診相談窓口へ') }}
    </a>
  </div>
</template>

<!-- v-html で展開される場所の翻訳待ちは 空文字ではなく 0 にする  -->
<i18n>
{
  "ja": {
    "{past}の出来ごとと症状": "{past}の出来ごとと症状",
    "発症前{two}週間以内": "発症前{two}週間以内",
    "発熱": "発熱",
    "または": "または",
    "呼吸器症状": "呼吸器症状",
    "かつ": "かつ",
    "発熱{temperature}以上": "発熱{temperature}",
    "{tempNum}以上": "{tempNum}以上",
    "37.5℃": "37.5℃",
    "新型コロナ受診相談窓口へ": "新型コロナ受診相談窓口へ"
  },
  "en": {
    "{past}の出来ごとと症状": "{past}, if you have...",
    "発症前{two}週間以内": "In the past {two} weeks",
    "発熱": "Fever",
    "または": "or",
    "呼吸器症状": "Having respiratory symptoms",
    "かつ": "and",
    "発熱{temperature}以上": "body temperature {temperature}",
    "{tempNum}以上": "above {tempNum}",
    "37.5℃": "37.5℃",
    "新型コロナ受診相談窓口へ": ""
  },
  "zh-cn": {
    "{past}の出来ごとと症状": "如果您在{past}有过以下情况或症状",
    "発症前{two}週間以内": "发病前{two}周内",
    "発熱": "发烧",
    "または": "或者",
    "呼吸器症状": "呼吸道症状",
    "かつ": "和",
    "発熱{temperature}以上": "发烧 {temperature}",
    "{tempNum}以上": "{tempNum} 以上",
    "37.5℃": "37.5℃",
    "新型コロナ受診相談窓口へ": ""
  },
  "zh-tw": {
    "{past}の出来ごとと症状": "{past} 如果您有以下症狀",
    "発症前{two}週間以内": "發病前{two}週內",
    "発熱": "發燒",
    "または": "或者是",
    "呼吸器症状": "呼吸道症狀",
    "かつ": "以及",
    "発熱{temperature}以上": "發燒 {temperature}",
    "{tempNum}以上": "{tempNum} 以上",
    "37.5℃": "37.5℃",
    "新型コロナ受診相談窓口へ": ""
  },
  "ko": {
    "{past}の出来ごとと症状": "{past}의 증세",
    "発症前{two}週間以内": "발병전{two}주이내",
    "発熱": "발열",
    "または": "혹은",
    "呼吸器症状": "호흡기 증상",
    "かつ": "또는",
    "発熱{temperature}以上": "{temperature} 발열",
    "{tempNum}以上": "{tempNum} 이상의",
    "37.5℃": "37.5도",
    "新型コロナ受診相談窓口へ": ""
  },
  "ja-basic": {
    "{past}の出来ごとと症状": 0,
    "発症前{two}週間以内": 0,
    "発熱": "ねつが あるひと",
    "または": "",
    "呼吸器症状": "いきがつらいひと、むねがくるしい・ぜいぜいするひと",
    "かつ": "",
    "発熱{temperature}以上": "{temperature} たかいねつが あるひと",
    "{tempNum}以上": "{tempNum}より",
    "37.5℃": "37.5℃",
    "新型コロナ受診相談窓口へ": ""
  }
}
</i18n>

<style module lang="scss">
.SpPast {
  color: $gray-2;
  .Heading {
    @include font-size(20);
    text-align: center;
    margin-bottom: 0.5em;
    strong {
      @include font-size(32);
    }
    .small {
      @include font-size(16);
    }
  }
  p {
    @include font-size(20);
    text-align: center;
    font-weight: bold;
    .small {
      @include font-size(16);
      color: $green-1;
    }
    .underline {
      display: inline-block;
      border-bottom: $green-1 4px solid;
    }
  }
  .flexContainer {
    display: flex;
    font-weight: bold;
    @include font-size(18);
    justify-content: space-between;
    .item {
      @include font-size(18);
      line-height: 1rem;
      text-align: center;
      &:nth-child(1),
      &:nth-child(3) {
        width: 7rem;
        > div {
          height: 3.5rem;
          border: $green-1 2px solid;
          border-radius: 5px;

          // 上下中央寄せ
          display: flex;
          justify-content: center;
          align-items: center;

          // before要素の親要素
          position: relative;
          &::before {
            width: 24px;
            height: 24px;
            content: '';
            background-color: $white;
            background-image: url(/flow/check_circle-24px.svg);
            position: absolute;
            top: -12px;
            left: 0;
            right: 0;
            margin: auto;
          }
          &.block {
            display: block;
          }
        }
      }
      &:nth-child(2) {
        // 上下中央寄せ
        display: flex;
        align-items: center;
      }
      .small {
        @include font-size(12);
      }
    }
  }
  .hr {
    border-bottom: 1px $gray-4 solid;
    height: 1px;
    width: 100%;
    display: block;
  }
  .counter {
    background-color: #ffe200;
    border-radius: 4px;
    box-shadow: -1px 2px 5px $gray-3;
    display: block;
    position: relative;
    text-decoration: none;
    color: $gray-2;
    font-weight: bold;
    @include font-size(18);
    &::after {
      width: 45px;
      height: 45px;
      background-image: url(/flow/arrow_forward-24px.svg);
      background-position: right center;
      background-repeat: no-repeat;
      transform: rotateZ(90deg);
      content: '';
      display: block;
      position: absolute;
      right: 8px;
      top: 4px;
    }
  }
}
</style>
