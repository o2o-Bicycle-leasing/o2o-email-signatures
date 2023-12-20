<template>
  <div>
    <br>
    <div ref="raw" v-show="false">
        <mjml>
            <mj-head>
                <mj-font name="Poppins" href="https://fonts.googleapis.com/css?family=Poppins:100,100italic,200,200italic,300,300italic,regular,italic,500,500italic,600,600italic,700,700italic,800,800italic,900,900italic" />
                <mj-font name="Roboto" href="https://fonts.googleapis.com/css?family=Roboto:100,100italic,300,300italic,regular,italic,500,500italic,700,700italic,900,900italic" />
            </mj-head>
        <mj-body>
            <mj-section>
                <mj-column>
                    <mj-image border-radius="120px" width="120px" :src="parseImg(person.img)"></mj-image>
                </mj-column>
                <mj-column>
                    <mj-text font-family="Poppins" padding="0px" color="#1b1b1f" font-size="20px" font-weight="600" line-height="20px">{{ person.name }}</mj-text>
                    <mj-text font-family="Poppins" padding="0px" padding-top="4px" color="#1b1b1f" font-size="13px" font-weight="400" line-height="20px">{{ person.title }}</mj-text>
                    <mj-divider border-width="1px" border-color="#eab1df" width="32px" padding="16px 0" align="left"></mj-divider>
                    <mj-text padding="0px"  color="#1b1b1f">General: <a style="color:#336650 !important; text-decoration: none !important;" href="tel:+3292964012">+32 9 296 40 12</a></mj-text>
                    <mj-text padding="0px"  color="#1b1b1f">{{ person.phone }}</mj-text>
                </mj-column>
            </mj-section>
        </mj-body>
        </mjml>
    </div>
    <div style="display: table;width:600px" ref="html" v-html="compiled">

    </div>
    <div style="height: 240px"></div>
  </div>
</template>

<script>
  import mjml2html from "mjml-browser";
  export default {
    name: "Signature",
    props: ['person', 'html', 'language'],
    data() {
      return {
        compiled: '',
      }
    },
    mounted() {
      this.compiled = mjml2html(this.$refs.raw.innerHTML).html
    },
    methods: {
      getPhoneLabelForLang(lang) {
        if (lang === 'fr') {
          return 'Général:';
        }

        if (lang === 'en') {
          return 'General:';
        }

        return "Alg.:";
      },
      getLogo() {
        return "https://www.o2o.be/app/uploads/2023/01/Logo-website-1.png";
      },
      getUrlForLang(lang) {
        if (lang === 'fr') {
          return "https://www.o2o.be/fr/nouvelles/o2o-vainqueur-dans-la-categorie-mobilite-du-deloitte-fast-50/";
        }
        if (lang === 'en') {
          return "https://www.o2o.be/en/news/o2o-winner-of-deloittes-fast-50-mobility-category/";
        }

        return "https://www.o2o.be/nl/fietsnieuws/o2o-wint-categorie-mobiliteit-deloitte-fast-50/";
      },
      parseImg(img) {
        if (img.includes('http')) {
          return img;
        }

        return 'https://signatures.o2o.be' + img;
      },
      getFooterTextForLang(lang) {
        if (lang === 'fr') {
          return `"o2o est à nouveau primé au Deloitte Technology Fast 50 2022 : nous sommes arrivés en tête dans la catégorie 'Mobilité' pour la seconde année consécutive." - <span style="font-size: 7pt; text-decoration: underline;">lisez notre blog</span>`;
        }
        if (lang === 'en') {
          return `"o2o is once again among the winners of this year's Deloitte Technology Fast 50 and comes out on top of the 'Mobility' category for the second year in a row." - <span style="font-size: 7pt; text-decoration: underline;">read our blog</span>`;
        }

        return `"o2o valt dit jaar opnieuw in de prijzen in Deloitte’s Technology Fast 50 en komt voor het tweede jaar op rij als beste uit de bus in de categorie ‘Mobiliteit’." - <span style="font-size: 7pt; text-decoration: underline;">lees onze blog</span>`;
      },
      hrefify(phone) {
        return 'tel:' + phone.replace(' ', '');
      }
    }
  }
</script>
<style>
