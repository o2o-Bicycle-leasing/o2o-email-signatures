<template>
  <div>
    <br>
    <div style="display: table;width:600px" ref="html">
      <table width="600px" role="presentation" cellspacing="0" cellpadding="0" border="0" align="left" style="border-collapse: collapse !important; border-spacing: 0 !important;">
        <tbody>
        <tr>
          <td style="width:88px;height:88px;direction:ltr;font-size:0px;text-align:center;padding:0px;background-color:#C5ECC1 !important;"  v-if="person.img">
            <img :src="person.img" height="88" width="88" alt=""
                 style="border:none;display:block;outline:none;height:88px;width:88px;padding-left:8px;object-fit: cover;border-radius: 50%;"
                 class="CToWUd">
          </td>
          <td :width="person.img ? '368px' : '480px'" style="height:112px;direction:ltr;font-size:0px;padding:0px;vertical-align:top;background-color:#C5ECC1;color:#336650 !important" :colspan="person.img ? 1 : 2">
            <table width="100%" role="presentation" cellspacing="0" cellpadding="0" border="0">
              <tbody>
              <tr>
                <td style="vertical-align:middle;padding:0 8px;">
                  <table width="100%" role="presentation" cellspacing="0" cellpadding="0" border="0">
                    <tbody>
                    <tr><td style="height: 8px;"></td></tr>
                    <tr>
                      <td width="100%" align="left" style="padding:0px;word-break:break-word">
                          <span style="font-family:Verdana,Helvetica,Arial,sans-serif;font-size:14pt;font-weight:bold;line-height:1.55;">
                            <font color="#336650"><b>{{ person.name }}</b></font>
                          </span>
                      </td>
                    </tr>
                    <tr>
                      <td width="100%" align="left" style="padding:0px 0px 4px;word-break:break-word">
                          <span style="font-family:Verdana,Helvetica,Arial,sans-serif;font-size:10pt;line-height:1.55;">
                              <font color="#336650">{{ person.title || '&nbsp;' }}</font>
                          </span>
                      </td>
                    </tr>
                    <tr align="left" style="padding:0px;word-break:break-word">
                      <td width="100%" align="left" style="padding:0px 0px 4px;word-break:break-word">
                        <table width="100%">
                          <tbody>
                          <tr>
                            <td style="width:34px;white-space:nowrap !important;">
                                <span style="font-family:Verdana,Helvetica,Arial,sans-serif;font-size:7pt;">
                                  <span v-if="person.phone" style="color:#336650 !important">Direct:</span>
                                </span>
                            </td>
                            <td style="width:140px;white-space:nowrap !important;">
                                <span style="font-family:Verdana,Helvetica,Arial,sans-serif;font-size:7pt;">
                                  <a style="color:#336650 !important; text-decoration: none !important;" v-if="person.phone" :href="hrefify(person.phone)">{{ person.phone }}</a>
                                </span>
                            </td>
                            <td style="width: 140px;white-space:nowrap !important;">
                                <span style="font-family:Verdana,Helvetica,Arial,sans-serif;font-size:7pt;">
                                    <a style="color:#336650 !important; text-decoration: none !important;" href="https://www.o2o.be/">www.o2o.be</a>
                                </span>
                            </td>
                          </tr>
                          <tr>
                            <td style="width:34px;white-space:nowrap !important;">
                                <span style="font-family:Verdana,Helvetica,Arial,sans-serif;font-size:7pt;">
                                  <span style="color:#336650 !important">{{ getPhoneLabelForLang(language) }}</span>
                                </span>
                            </td>
                            <td style="width:140px;white-space:nowrap !important;">
                                <span style="font-family:Verdana,Helvetica,Arial,sans-serif;font-size:7pt;">
                                    <a style="color:#336650 !important; text-decoration: none !important;" href="tel:+3292964012">+32 9 296 40 12</a>
                                </span>
                            </td>
                            <td style="width:140px;white-space:nowrap !important;">
                                <span style="font-family:Verdana,Helvetica,Arial,sans-serif;font-size:7pt;">
                                    <a style="color:#336650 !important; text-decoration: none !important;" href="https://www.google.be/maps/place/o2o+-+Company+bike+lease+-+We+make+you(r)+ride+easier/@51.0887261,3.7418109,17z/data=!3m1!4b1!4m5!3m4!1s0x47c376b6afac42a9:0xc962d1354b36a8bd!8m2!3d51.0887269!4d3.7440127">Farmanstraat 40, 9000 Gent</a>
                                </span>
                            </td>
                          </tr>
                          </tbody>
                        </table>
                      </td>
                    </tr>
                    </tbody>
                  </table>
                </td>
              </tr>
              </tbody>
            </table>
          </td>
          <td style="width:140px;height:30px;direction:ltr;font-size:0px;text-align:center;background-color:#a7d0fa !important;" colspan="2">
            <img :src="getLogoForLang(language)" width="90" :height="(language === 'nl') ? 33 : 31" style="max-width: 100%" />
          </td>
        </tr>
        <tr>
          <td colspan="3" style="padding:8px 20px;background-color: #ffeb9d !important;width:517px;">
            <a style="color:#b67b16 !important; text-decoration: none !important; font-family:Verdana,Helvetica,Arial,sans-serif;font-size:9pt;" :href="getUrlForLang(language)" v-html="getFooterTextForLang(language)">
            </a>
          </td>
          <td style="background-color: #ffeb9d !important; text-align: right !important; width: 83px;">
            <img src="https://www.o2o.be/app/uploads/2022/02/sig_cog.png" height="82" width="83" style="vertical-align: bottom" />
          </td>
        </tr>
        </tbody>
      </table>
      <br><br><br><br><br><br>
      <br><br><br><br><br><br>
    </div>
    <textarea v-if="html" v-model="content" disabled style="width: 600px; height: 300px;" />
    <div style="height: 240px"></div>
  </div>
</template>

<script>
  export default {
    name: "Signature",
    props: ['person', 'html', 'language'],
    data() {
      return {
        content: '',
      }
    },
    mounted() {
      this.content = this.$refs.html.innerHTML;
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
      getLogoForLang(lang) {
        if (lang === 'fr') {
          return "https://www.o2o.be/app/uploads/2022/09/sig_logo_fr.png";
        }
        if (lang === 'en') {
          return "https://www.o2o.be/app/uploads/2022/09/sig_logo_en.png";
        }

        return "https://www.o2o.be/app/uploads/2022/02/sig_logo-e1643707682115.png";
      },
      getUrlForLang(lang) {
        if (lang === 'fr') {
          return "https://www.o2o.be/fr/nouvelles/technology-fast-50-de-deloitte/";
        }
        if (lang === 'en') {
          return "https://www.o2o.be/en/news/deloitte-technology-fast-50/";
        }

        return "https://www.o2o.be/nl/fietsnieuws/deloitte-technology-fast-50-8ste-editie/";
      },
      getFooterTextForLang(lang) {
        if (lang === 'fr') {
          return `"o2o arrive en tête du Technology Fast 50 2021 de Deloitte, la liste des cinquante entreprises technologiques à la croissance le plus rapide en Belgique" - <span style="font-size: 7pt; text-decoration: underline;">en savoire plus</span>`;
        }
        if (lang === 'en') {
          return `"o2o comes out on top in Deloitte's 2021 Technology Fast 50, the list of the fifty fastest-growing technology companies in Belgium" - <span style="font-size: 7pt; text-decoration: underline;">read more</span>`;
        }

        return `"o2o komt als beste uit de bus in Deloitte's 2021 Technology Fast 50, de lijst van de vijftig snelst groeiende technologiebedrijven in België" - <span style="font-size: 7pt; text-decoration: underline;">lees meer</span>`;
      },
      hrefify(phone) {
        return 'tel:' + phone.replace(' ', '');
      }
    }
  }
</script>
