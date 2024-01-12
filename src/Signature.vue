<template>
  <div>
    <br>
    <div ref="raw" v-show="false" style="padding: 0 18px">
        <mjml>
            <mj-head>
                <mj-font name="Poppins" href="https://fonts.googleapis.com/css?family=Poppins:100,100italic,200,200italic,300,300italic,regular,italic,500,500italic,600,600italic,700,700italic,800,800italic,900,900italic" />
                <mj-attributes>
                  <mj-all font-family="Poppins, Arial, sans-serif" />
                </mj-attributes>
                <mj-breakpoint width="600px" />
                <mj-html-attributes>
                  <mj-selector path=".no-padding > div">
                    <mj-html-attribute name="style">padding: 0; width: 600px;</mj-html-attribute>
                  </mj-selector>
                </mj-html-attributes>
            </mj-head>
        <mj-body css-class="no-padding">
            <mj-section padding="0px 0px 18px 0px" text-align="left">
                <mj-column v-if="person.img" vertical-align="middle" width="120px" padding="0px 0px 20px 20px">
                    <mj-image align="left" border-radius="120px" width="120px" padding="0" :src="parseImg(person.img, 100, 150, cover)"></mj-image>
                </mj-column>
                <mj-column vertical-align="middle" padding="0px 0px 20px 20px">
                    <mj-text font-family="Poppins, Arial, sans-serif" padding="0px" color="#1b1b1f" font-size="20px" font-weight="600" line-height="20px">{{ person.name }}</mj-text>
                    <mj-text font-family="Poppins, Arial, sans-serif" padding="0px" padding-top="4px" color="#1b1b1f" font-size="13px" font-weight="400" line-height="20px">{{ person.title }}</mj-text>
                    <mj-divider border-width="2px" border-color="#eab1df" width="32px" padding="16px 0" align="left"></mj-divider>
                    <mj-text padding="0px" color="#1b1b1f" font-size="10px" line-height="16px" font-weight="400" font-family="Poppins, Arial, sans-serif"><a style="color: #1b1b1f !important; text-decoration: none !important;" href="https://www.o2o.be">o2o.be</a></mj-text>
                    <mj-text padding="0px"  color="#1b1b1f" font-size="10px" line-height="16px" font-weight="400" font-family="Poppins, Arial, sans-serif">General: <a style="color: #1b1b1f !important; text-decoration: none !important;" href="tel:+3292964012">+32 9 296 40 12</a></mj-text>
                    <mj-text v-if="person.phone" padding="0px"  color="#1b1b1f" font-size="10px" line-height="16px" font-weight="400" font-family="Poppins, Arial, sans-serif">Direct: <a style="color: #1b1b1f !important; text-decoration: none !important;" :href="hrefify(person.phone)">{{ person.phone }}</a></mj-text>
                </mj-column>
            </mj-section>
            <mj-section background-color="#f5f6fe" padding="0 24px 8px" border-radius="8px">
                <mj-column width="164px" align="left" padding="16px 0 8px">
                  <mj-image align="left" width="135px" height="42px" padding="5px 0" :src="parseImg('/icons/logo.png')"></mj-image>
                </mj-column>
                <mj-column width="292px"></mj-column>
                <mj-column width="96px" align="left" padding="20px 0 8px">
                  <mj-raw>
                    <div style="color: #47464a; font-family: Poppins, sans-serif; font-size:12px; font-weight:400; line-height:20px; text-align: left;">stay connected</div>
                    <table cellpadding="0" cellspacing="0" border="0" class="frame-7" style="border-collapse: collapse; width: 96px;">
                      <tr>
                        <td>
                          <a href="https://www.linkedin.com/company/o2o-be/" class="w-inline-block">
                            <img :src="parseImg('/icons/linkedin.png')" width="20" height="20" alt="" style="padding: 2px; padding-left: 0px;" class="social-media-icons" />
                          </a>
                        </td>
                        <td>
                          <a href="https://www.facebook.com/o2o.be/" class="w-inline-block">
                            <img :src="parseImg('/icons/facebook.png')" width="20" height="20" alt="" style="padding: 2px;" class="social-media-icons" />
                          </a>
                        </td>
                        <td>
                          <a href="https://www.instagram.com/o2o.be/" class="w-inline-block">
                            <img :src="parseImg('/icons/instagram.png')" width="20" height="20" style="padding: 2px;" alt="" class="social-media-icons" />
                          </a>
                        </td>
                        <td>
                          <a href="https://www.youtube.com/channel/UC7BnVDfVdUoeYLuHxysmV9w/videos" class="w-inline-block">
                            <img :src="parseImg('/icons/youtube.png')" width="20" height="20" style="padding: 2px;" alt="" class="social-media-icons" />
                          </a>
                        </td>
                      </tr>
                    </table>
                  </mj-raw>
                </mj-column>
                <mj-table>
                    <tr>
                        <td width="100%" style="width:100%;"></td>
                        <td width="96px" style="width: 96px">

                        </td>
                    </tr>
                </mj-table>
              </mj-section>
        </mj-body>
        </mjml>
    </div>
    <div style="display: table; width: 100%;" ref="html" v-html="compiled">

    </div>
    <div style="height: 140px"></div>
  </div>
</template>

<script>
  import mjml2html from "mjml-browser";
  export default {
    name: "Signature",
    props: ['person'],
    data() {
      return {
        compiled: '',
      }
    },
    mounted() {
      if (this.$refs.raw?.innerHTML) {
        this.compiled = mjml2html(this.$refs.raw.innerHTML).html + '<br/><br/>'
      }
    },
    methods: {
      getUrlForLang(lang) {
        if (lang === 'fr') {
          return "https://www.o2o.be/fr/nouvelles/o2o-vainqueur-dans-la-categorie-mobilite-du-deloitte-fast-50/";
        }
        if (lang === 'en') {
          return "https://www.o2o.be/en/news/o2o-winner-of-deloittes-fast-50-mobility-category/";
        }

        return "https://www.o2o.be/nl/fietsnieuws/o2o-wint-categorie-mobiliteit-deloitte-fast-50/";
      },
      parseImg(img, w, h, fit) {
        if (!img) {
          return img;
        }

        if (img.includes('http')) {
          return img;
        }

        if (process?.env?.NODE_ENV === 'development') {
          return 'http://localhost:8080' + img;
        }

        if (w || h || fit) {
          return `https://signatures.o2o.be/.netlify/images?url=${img}&w=${w}&h=${h}&fit=${fit}`;
        }

        return 'https://signatures.o2o.be' + img;
      },
      hrefify(phone) {
        return 'tel:' + phone.replace(' ', '');
      }
    }
  }
</script>
<style>
