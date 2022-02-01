<template>
  <div id="app">
    <div v-for="(person, i) in data" :key="i">
      <div style="display: table;width: 100%;">
        <table width="600px" role="presentation" cellspacing="0" cellpadding="0" border="0" align="left" style="border-collapse: collapse !important; border-spacing: 0 !important;">
          <tbody>
          <tr>
            <td style="height:112px;direction:ltr;font-size:0px;text-align:center;padding:0px;background-color:#C5ECC1 !important;"  v-if="person.img">
              <img :src="person.img" height="88" width="88" alt=""
                   style="border:none;display:block;outline:none;height:88px;width:88px;padding-left:8px;object-fit: cover;border-radius: 50%;"
                   class="CToWUd">
            </td>
            <td style="width:375px;height:112px;direction:ltr;font-size:0px;padding:0px;vertical-align:top;background-color:#C5ECC1;color:#336650 !important" :colspan="person.img ? 1 : 2">
              <table width="100%" role="presentation" cellspacing="0" cellpadding="0" border="0">
                <tbody>
                <tr>
                  <td style="vertical-align:middle;padding:8px 16px;">
                    <table width="100%" role="presentation" cellspacing="0" cellpadding="0" border="0">
                      <tbody>
                      <tr>
                        <td align="left" style="padding:0px;word-break:break-word">
                          <span style="font-family:Verdana,Helvetica,Arial,sans-serif;font-size:14pt;font-weight:bold;line-height:1.55;">
                            <font color="#336650"><b>{{ person.name }}</b></font>
                          </span>
                        </td>
                      </tr>
                      <tr>
                        <td align="left" style="padding:0px 0px 4px;word-break:break-word">
                          <span style="font-family:Verdana,Helvetica,Arial,sans-serif;font-size:10pt;line-height:1.55;">
                              <font color="#336650">{{ person.title || '&nbsp;' }}</font>
                          </span>
                        </td>
                      </tr>
                      <tr align="left" style="padding:0px;word-break:break-word">
                        <td align="left" style="padding:0px 0px 4px;word-break:break-word">
                          <table>
                            <tbody>
                            <tr>
                              <td style="width:34px">
                                <span style="font-family:Verdana,Helvetica,Arial,sans-serif;font-size:7pt;">
                                  <span v-if="person.phone" style="color:#336650 !important">Direct:</span>
                                </span>
                              </td>
                              <td style="width:140px">
                                <span style="font-family:Verdana,Helvetica,Arial,sans-serif;font-size:7pt;">
                                  <a style="color:#336650 !important; text-decoration: none !important;" v-if="person.phone" :href="hrefify(person.phone)">{{ person.phone }}</a>
                                </span>
                              </td>
                              <td>
                                <span style="font-family:Verdana,Helvetica,Arial,sans-serif;font-size:7pt;">
                                    <a style="color:#336650 !important; text-decoration: none !important;" href="https://www.o2o.be/">www.o2o.be</a>
                                </span>
                              </td>
                            </tr>
                            <tr>
                              <td style="width:34px">
                                <span style="font-family:Verdana,Helvetica,Arial,sans-serif;font-size:7pt;">
                                  <span style="color:#336650 !important">Alg.:</span>
                                </span>
                              </td>
                              <td style="width:140px">
                                <span style="font-family:Verdana,Helvetica,Arial,sans-serif;font-size:7pt;">
                                    <a style="color:#336650 !important; text-decoration: none !important;" href="tel:+3292964012">+32 9 296 40 12</a>
                                </span>
                              </td>
                              <td>
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
            <td style="height:112px;direction:ltr;font-size:0px;text-align:center;padding:0px 20px;background-color:#a7d0fa !important;">
              <img src="https://www.o2o.be/app/uploads/2022/02/sig_logo-e1643707682115.png" width="100" height="37" />
            </td>
          </tr>
          <tr>
            <td colspan="2" style="padding:0 20px;background-color: #ffeb9d !important;">
              <a style="color:#b67b16 !important; text-decoration: none !important; font-family:Verdana,Helvetica,Arial,sans-serif;font-size:9pt;" href="https://www.o2o.be/nl/fietsnieuws/deloitte-technology-fast-50-8ste-editie/">
                "o2o komt als beste uit de bus in Deloitte's 2021 Technology Fast 50, de lijst van de vijftig snelstgroeiende techonolgiebedrijven in België"
              </a>
            </td>
            <td style="background-color: #ffeb9d !important; text-align: right !important;">
              <img src="https://www.o2o.be/app/uploads/2022/02/sig_cog.png" height="82" width="83" style="vertical-align: bottom" />
            </td>
          </tr>
          </tbody>
        </table>
        <br>
        <br>
      </div>
      <div style="height: 240px"></div>
    </div>
  </div>
</template>

<script>
import data from "./data.js";

export default {
  name: 'App',
  data: function () {
    console.log(data);
    return {
      data: data,
    }
  },
  methods: {
    hrefify(phone) {
      return 'tel:' + phone.replace(' ', '');
    }
  }
}
</script>
