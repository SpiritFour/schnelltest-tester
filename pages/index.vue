<template>
  <v-container>
    <h1 class="text-h2 font-weight-bold text-center my-5">
      {{ validSchnelltests + invalidSchnelltests }} Schnelltests -
      {{ validSchnelltests }} erkennen Omicron
    </h1>

    <v-combobox
      :placeholder="search || 'Schnelltest eingeben'"
      class="mt-16 text-h5 py-4"
      dense
      filled
      rounded
      :items="schnelltests"
      :search-input.sync="search"
    >
    </v-combobox>

    <Schnelltest
      :test="test"
      v-for="test in matchedSchnelltests"
      :key="test['name'] + test.manufacturer"
    />
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      search: '',
      schnelltests: [
        {
          manufacturer: 'Absology Co.,Ltd.',
          name: 'INIST COVID-19 Ag Rapid',
          'omicron-sensitive': false,
        },
        {
          manufacturer: 'Acro Biotech, Inc.',
          name: 'Acro COVID-19 Antigen Rapid Test',
          'omicron-sensitive': false,
        },
        {
          manufacturer: 'Aikang Diagnostics Co., Ltd.',
          name: 'SARS-CoV-2 Antigen Test Kit (Immunochromatography)',
          'omicron-sensitive': false,
        },
        {
          manufacturer: 'Beijing Savant Biotechnology Co., Ltd.',
          name: 'New Coronavirus (SARS-CoV-2) N Protein Detection Kit (Fluorescence Immunchromatography)',
          'omicron-sensitive': false,
        },
        {
          manufacturer: 'Biopanda Reagents',
          name: 'COVID-19 Antigen-Schnelltest',
          'omicron-sensitive': false,
        },
        {
          manufacturer: 'CertestT Biotec S. L.',
          name: 'CerTest Biotec SARS-CoV-2 Ag Test',
          'omicron-sensitive': false,
        },
        {
          manufacturer: 'Changsha Sanji Bio-technology Co., Ltd',
          name: 'SARS-CoV-2 Antigen Rapid Test (Laterial Flow Method)',
          'omicron-sensitive': false,
        },
        {
          manufacturer: 'Coris BioConcept',
          name: 'COVID-19 Ag Respi-Strip',
          'omicron-sensitive': false,
        },
        {
          manufacturer: 'Dejavu Medikal San. Ve Tic. Ltd. Sti.',
          name: 'COVID-19 Antigen Schnelltest',
          'omicron-sensitive': false,
        },
        {
          manufacturer: 'Diasia Biomedical Technology Co., Ltd.',
          name: 'DIASIA SARS-CoV-2 Antigen Rapid Test Kit',
          'omicron-sensitive': false,
        },
        {
          manufacturer: 'Essa Commerce Bilisim ve Ithalat Ihracat Tic.A.S.',
          name: 'Bioessa SARS-CoV-2 Antigen Schnelltest',
          'omicron-sensitive': false,
        },
        {
          manufacturer: 'FAGO MEDIKAL San. Tic. Ltd',
          name: 'FAMEX® SARS-CoV-2 Ag Rapid Nasopharyngeal Test Kit',
          'omicron-sensitive': false,
        },
        {
          manufacturer: 'Foregene Co.,Ltd.',
          name: 'FOREGENE SARS-CoV-2 Antigen Test Kit',
          'omicron-sensitive': false,
        },
        {
          manufacturer: 'Hangzhou AllTest Biotech Co. Ltd.',
          name: 'COVID-19 Antigen Rapid Test (Nasopharyngeal swab)',
          'omicron-sensitive': false,
        },
        {
          manufacturer: 'Hangzhou Bioer Technology Co., Ltd.',
          name: 'BIOflux SARS-CoV-2 Antigen Test Kit (colloidal gold method)',
          'omicron-sensitive': false,
        },
        {
          manufacturer: 'Hangzhou Biotest Biotech Co., Ltd.',
          name: 'Lumiratek SARS-CoV-2 Antigen Rapid Test Cassette',
          'omicron-sensitive': false,
        },
        {
          manufacturer: 'Hangzhou Fanttest Biotech Co.,Ltd.',
          name: 'Fanttest Novel Coronavirus(SARS-CoV-2) Antigen Rapid Test Cassette',
          'omicron-sensitive': false,
        },
        {
          manufacturer: 'Hangzhou Realy Tech Co., Ltd.',
          name: 'Novel Coronavirus (SARS-Cov-2) Antigen Rapid Test Cassette (swab)',
          'omicron-sensitive': false,
        },
        {
          manufacturer: 'Hangzhou Realy Tech Co., Ltd.',
          name: 'Heinzer Antigen Covid19 Spucktest Schnelltest [Original Name: Novel Coronavirus (SARS-CoV-2) Antigen Rapid Test Device (saliva)]',
          'omicron-sensitive': false,
        },
        {
          manufacturer: 'Hangzhou Singclean Medical Products Co., Ltd.',
          name: 'COVID-19 Test Kit (Colloidal Gold Method)',
          'omicron-sensitive': false,
        },
        {
          manufacturer: 'Hangzhou Genesis Biocontrol Co., Ltd',
          name: 'KaiBiLi COVID-19 Antigen Rapid Test Device',
          'omicron-sensitive': false,
        },
        {
          manufacturer: 'Inzek International Trading B.V',
          name: 'BIOZEK COVID-19-Antigen-Schnelltestkassette',
          'omicron-sensitive': false,
        },
        {
          manufacturer: 'Joinstar Biomedical Technology Co., Ltd',
          name: 'COVID-19 Antigen Rapid Test (Latex)',
          'omicron-sensitive': false,
        },
        {
          manufacturer: 'Joysbio (Tianjin) Biotechnology Co., Ltd.',
          name: 'Joysbio SARS-CoV-2 Antigen Rapid Test Kit (Colloidal Gold)',
          'omicron-sensitive': false,
        },
        {
          manufacturer: 'Koch Biotechnology (Beijing) Co., Ltd.',
          name: 'COVID-19 Antigen Rapid Test Kit',
          'omicron-sensitive': false,
        },
        {
          manufacturer: 'LiClear Biotech (Hangzhou) Co., Ltd.',
          name: 'SARS-COV-2 Nucleocapsid (N) Antigen Rapid Test (VIDA TEST Rapid Diagnostic Test)',
          'omicron-sensitive': false,
        },
        {
          manufacturer: 'Lionex GmbH',
          name: 'Lionex COVID-19 Ag Rapid Test',
          'omicron-sensitive': false,
        },
        {
          manufacturer: 'Medicon Co., Ltd.',
          name: 'Trueline COVID-19 Ag Rapid Test',
          'omicron-sensitive': false,
        },
        {
          manufacturer: 'Mexacare GmbH Heidelberg',
          name: 'QuickTestCorona COVID-19 Antigen Schnelltest',
          'omicron-sensitive': false,
        },
        {
          manufacturer: 'nal von minden GmbH',
          name: 'dedicio Medical Test COVID-19 Ag plus Test',
          'omicron-sensitive': false,
        },
        {
          manufacturer: 'RapiGEN, Inc.',
          name: 'Biocredit COVID-19 Ag',
          'omicron-sensitive': false,
        },
        {
          manufacturer: 'Redcell Bioteknoloji Anim Sirketi',
          name: 'COVID-19 Antigen Test',
          'omicron-sensitive': false,
        },
        {
          manufacturer: 'Servoprax GmbH',
          name: 'Cleartest Corona-Antigen',
          'omicron-sensitive': false,
        },
        {
          manufacturer: 'SG Diagnostics Pte Ltd',
          name: 'SG Diagnostics COVID-19 Antigen Rapid Test Kit (Colloidal Gold-Based)',
          'omicron-sensitive': false,
        },
        {
          manufacturer: 'ShanDong ThinkLabor Biotechnology Co.,Ltd.',
          name: 'Coronavirus Ag Schnelltest Kassette (Tupfer)',
          'omicron-sensitive': false,
        },
        {
          manufacturer: 'Shenzhen Landwind Biotechnology Co., Ltd.',
          name: 'Landwind SARS-CoV-2 Antigen Test Kit (Colloidal Gold)',
          'omicron-sensitive': false,
        },
        {
          manufacturer: 'Spring Healthcare Services Sp zoo',
          name: 'SARS-Cov-2 Antigen Rapid Test Cassette (swab)',
          'omicron-sensitive': false,
        },
        {
          manufacturer: 'SureScreen Diagnostics Ltd.',
          name: 'COVID-19 Antigen Rapid Test Cassette',
          'omicron-sensitive': false,
        },
        {
          manufacturer: 'TaiDoc Technology Corporation',
          name: 'FORA COVID-19 ANTIGEN RAPID TEST',
          'omicron-sensitive': false,
        },
        {
          manufacturer: 'Unioninvest',
          name: 'Unibioscience COVID-19 Rapid Antigen Test',
          'omicron-sensitive': false,
        },
        {
          manufacturer:
            'Vision Biyoteknologi Arastirma Gelistirme Labt. Sist. San ve Tic LTD STI',
          name: 'VISION® SARS-CoV-2 Saliva Antigen Rapid Test Kit',
          'omicron-sensitive': false,
        },
        {
          manufacturer: 'VivaChek Biotech (Hangzhou) Co., Ltd.',
          name: 'VivaDiag SARS-CoV-2 Ag Rapid Test',
          'omicron-sensitive': false,
        },
        {
          manufacturer: 'VivaChek Biotech (Hangzhou) Co., Ltd.',
          name: 'VivaDiag Pro SARS-CoV-2 Ag Rapid Test',
          'omicron-sensitive': false,
        },
        {
          manufacturer: 'W.H.P.M, Inc.',
          name: 'First Sign SARS-CoV-2 Antigen Test',
          'omicron-sensitive': false,
        },
        {
          manufacturer: 'Xiamen Jiqing Biomedical Technology Co., Ltd.',
          name: 'Gruenbanka SARS-CoV-2 Antigen detection Kit (colloidal gold method)',
          'omicron-sensitive': false,
        },
        {
          manufacturer: 'Xiamen Zhongsheng Langjie Biotechnology Co., Ltd',
          name: 'Covid-19 Antigen Test Cassette',
          'omicron-sensitive': false,
        },
        {
          manufacturer: 'Abbott Rapid Diagnostics Jena GmbH',
          name: 'PanbioTM COVID-19 Ag Rapid Test Device (NASOPHARYNGEAL)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Abioteq',
          name: 'Cora Gentest-19',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'AccuBioTech Co.,Ltd.',
          name: 'Accu-Tell Rapid In-vitro Diagnostiktest',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'ACON Biotech (Hangzhou) Co., Ltd',
          name: 'Flowflex SARS-CoV-2-Antigenschnelltest',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Acro Diagnostics Co., Ltd',
          name: 'SARS-CoV-2 Antigen Rapid Detection Kit (LFA)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Aesku Diagnostics GmbH',
          name: 'Aesku Rapid SARS-CoV-2 Rapid Test',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Affimedix',
          name: 'TestNOW® COVID-19-Antigen-Test',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Amazing Biotech (Shanghai) Co., Ltd',
          name: 'CoroVisio Covid-19 Ag Versieglungsröhrchen Teststreifen (Kolloidales Gold)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Ameda Labordiagnostik GmbH',
          name: 'AMP Rapid Test SARS-CoV-2 Ag',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Amper,Inc.',
          name: 'Amper COVID-19 Antigen Rapid Testing Kit (Colloidal Gold)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Anbio (Xiamen) Biotechnology Co., Ltd',
          name: 'Rapid Covid-19 Antigen Test (Colloidal Gold )',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Anhui Deepblue Medical Technology Co. , Ltd.',
          name: 'COVID-19 (SARS CoV-2) Antigen Test Kit (Colloidal Gold)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Anhui Formaster Biosci Co., Ltd',
          name: 'New Coronavirus (COVID-19) Antigen Rapid Test',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Artron Laboratories Inc.',
          name: 'COVID-19 Antigentest',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'ASAN PHARM.CO.,LTD.',
          name: 'Asan Easy Test COVID-19 Ag',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Assure Tech (Hangzhou) Co.,Ltd',
          name: 'ECOTEST COVID-19 Antigen Rapid Test Device',
          'omicron-sensitive': true,
        },
        {
          manufacturer:
            'Asterion Otel Insaat Bilisim Medikal Maden Tic.Ltd.Sti.',
          name: 'AS-check COVID-19 Antigen Schnelltest',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Atlas Link Technology Co.,Ltd.',
          name: 'Nova Test SARS-CoV-2 Antigen Rapid Test Kit',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Avalun',
          name: 'Ksmart® SARS-COV2 Antigen Rapid Test',
          'omicron-sensitive': true,
        },
        {
          manufacturer:
            'AXIOM Gesellschaft für Diagnostica und Biochemica mbI-I',
          name: 'Axiom Diagnostics COVID-19 Ag Schnelltest',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Azure Biotech Inc.',
          name: 'Dia Sure Covid-19 Antigen Rapid Test Device (Nasopharyngeal/Oropharyngeal Swab)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Becton Dickinson',
          name: 'BD VeritorTM System for Rapid Detection of SARS-CoV-2',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Beijing Beier Bioengineering Co., Ltd.',
          name: 'Covid-19 Antigen Schnelltest',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Beijing I-Ioma Biological Engineering Co., Ltd.',
          name: 'COVID-19 Antigen Test Kit',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Beijing I-Iotgen Biotech Co., Ltd.',
          name: 'Novel Coronavirus 2019-nCoV Antigen Test (Colloidal gold)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Beijing Jinwofu Bioengineering Technology Co.,Ltd.',
          name: 'Jinwofu Novel Coronavirus (SARS-COV-2) Antigen Rapid Test Kit',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Beijing Kewei Clinical Diagnostic Reagent Inc.',
          name: 'COVID-19 Antigen Rapid Test Kit',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Beijing Lepu Medical Technology Co., Ltd',
          name: 'SARS-CoV-2 Antigen Rapid Test Kit',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Beijing O&D Biotech Co., Ltd.',
          name: 'Covid-19 Antigen Rapid Test (Colloidal Gold)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Beijing Tigsun Diagnostics Co.;Ltd.',
          name: 'Tigsun COVID-19 Saliva Antigen Rapid Test',
          'omicron-sensitive': true,
        },
        {
          manufacturer:
            'Beijing Wantai Biological Pharmacy Enterprise Co., Ltd.',
          name: 'Wantai SARS-CoV-2 Ag Rapid Test (FIA)',
          'omicron-sensitive': true,
        },
        {
          manufacturer:
            'Beijing Wantai Biological Pharmacy Enterprise Co., Ltd.',
          name: 'Wantai SARS-CoV-2 Ag Schnelltest (Kolloidales Gold)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Biocan Diagnostics Inc.',
          name: 'Tell Me Fast Rapid Diagnostic Test',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'BioDetect (Xiamen) Biotechnology Co., Ltd',
          name: 'SARS-Cov-2-Antigen-Schnelltest-Karte',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Biohit I-Iealthcare (I-Iefei) Co., Ltd.',
          name: 'SARS-CoV-2 Antigen Rapid Test (Colloidal Gold Method)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'BioMaxima S.A.',
          name: 'SARS-CoV-2 Ag Rapid Test',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'BIOMERICA Inc.',
          name: 'COVID-19-Antigen-Schnelltest (Nasopharyngeal-Abstrich)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'BIONOTE',
          name: 'NowCheck® COVID-19 Ag Test',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'BioRepair GmbH',
          name: 'Covid 19 Antigen Schnelltest',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Bioscience (Tianjin) Diagnostic Technology Co., Ltd',
          name: 'Novel Coronavirus(2019-nCoV) Antigen Rapid Test',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'BIOSYNEX SWISS SA',
          name: 'BIOSYNEX COVID-19 Ag BSS',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'BioTeke Corporation (Wuxi) Co.,Ltd.',
          name: 'SARS-CoV-2 Antigen Test Kit (Colloidal Gold Method)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'BTNX, Inc.',
          name: 'Rapid Response COVID-19 Rapid Test Device',
          'omicron-sensitive': true,
        },
        {
          manufacturer:
            'Cesna Biyoteknoloji Arastirma Gelistirme Laboratuvar Sist.',
          name: 'Check Up SARS-CoV-2 Nasal Antigen Rapid Test',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Changzhou Biowin Pharmaceutical Co.,Ltd.',
          name: 'Novel Coronavirus(COVID-19) Antigen Test Kit (Colloidal Gold)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Chil Tibbi Mal. San. Tic. Ltd. Şti',
          name: 'COVID-19 Antigen Schnell Test (Nasopharyngeal / Oropharyngeal Tupfer Kassette)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Chongqing ISIA BIO-Technology Co.,Ltd',
          name: 'ISIA SARS-CoV-2 Antigen Rapid Test Kit',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Chongqing M&D Biotechnology Co. Ltd.',
          name: '2019-nCoV Antigen Test Kit',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'CITEST Diagnostics Inc.',
          name: 'COVID-19 Antigen Rapid Test (Oral Fluid)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Co-Innovation Biotech Co. Ltd',
          name: 'Whole Power One Step 2019-Novel Coronavirus(2019-nCoV) Antigen Test',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Convergent Technologies',
          name: 'Convergys® COVID-19 Rapid Antigen Test',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Core Technology Co., Ltd.',
          name: 'Canea COVID-19 Antigen Schnelltest',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'CTK Biotech, Inc.',
          name: 'OnSite COVID-19 Ag Rapid Test',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'DNA Diagnostic A/S.',
          name: 'Covid-19 Antigen Detection Kit',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Dräger Safety AG & Co. KGaA',
          name: 'Dräger Antigen Test SARS-CoV-2',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Dynamiker Biotechnology (Tianjin) Co., Ltd.',
          name: 'Dynamiker SARS-CoV-2 AG Rapid Test',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Edinburgh Genetics Limited',
          name: 'Edinburgh Genetics ActivXpress+ COVID-19 Antigen Complete Testing Kit',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Eurobio Scientific',
          name: 'EBS SARS-CoV-2 Ag Rapid Test',
          'omicron-sensitive': true,
        },
        {
          manufacturer:
            'Fosun Diagnostics (Shanghai) Co., Ltd (ehemals Shanghai Fosun Long March Medical Science Co., Ltd.)',
          name: 'Fosun Covid-19 Ag Card',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'FUJIFILM Corporation',
          name: 'FUJIFILM COVID-19 Ag Test',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Fujirebio Inc.(Mast Diagnostica GmbH)',
          name: 'ESPLINE® SARS-CoV-2',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'GenBody Inc.',
          name: 'GenBody COVID-19 Ag',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Genobio Pharmaceutical Co., Ltd.',
          name: 'Virusee® SARS-CoV-2 Antigen Rapid Test (Colloidal Gold) (Saliva/Swab)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Genrui Biotech Inc.',
          name: 'Genrui SARS-CoV-2 Antigen Test Kit (Colloidal Gold)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'GenSure Biotech Inc.',
          name: 'DIA-COVID® COVID-19 Ag Rapid Test Kit',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Getein Biotech, Inc.',
          name: 'One Step Test for SARS-CoV-2 Antigen (Colloidal Gold)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Glallergen CO., LTD.',
          name: 'Novel Corona Virus (2019-nCoV) Ag Rapid Test Kit',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Goldsite Diagnostics Inc.',
          name: 'Goldsite COVID-19 SARS-CoV-2 Antigen Kit (Colloidal Gold)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Green Cross Medical Science Corp. (Weko Pharma GmbH)',
          name: 'Genedia W Covid-19 Ag',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Guangdong Hecin Scientific,Inc.',
          name: '2019-nCoV Antigen Test Kit (colloidal gold method)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Guangdong Longsee Biomedical Co.,Inc.',
          name: 'Longsee 2019-nCoV Ag Rapid Detection Kit (Immuno-Chromatography)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Guangdong Wesail Biotech Co., Ltd.',
          name: 'COVID-19 Ag Test Kit',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Guangzhou Tebsun Bio-Tech Development Co., Ltd.',
          name: 'Tebsun 2019-nCoV Antigen Test Kit',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Guangzhou Wondfo Biotech Co. Ltd',
          name: 'Wondfo SARS-CoV-2 Antigen Test (Lateral Flow Method)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Hangzhou AllTest Biotech Co., Ltd.',
          name: 'Covid-19 Antigen Rapid Test (Oral fluid)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Hangzhou AllTest Biotech Co.,Ltd.',
          name: 'AllTest SARS-CoV-2 Antigen Rapid Test (Nasal Swab)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Hangzhou Biotest Biotech Co., Ltd',
          name: 'Sienna COVID-19 Antigen-Schnelltestkassette (Nasenabstrich)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Hangzhou Careomedic Tech Co., Ltd.',
          name: 'SARS-CoV-2-Antigen-Schnelltest',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Hangzhou Clongene Biotech Co., Ltd.',
          name: 'Clungene COVID-19 Antigen Rapid Test',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Hangzhou DIAN Biotechnology Co., Ltd.',
          name: 'GENEDIAN COVID-19 Antigen Test Cassette',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Hangzhou Funworld Biotech. Co., Ltd',
          name: 'SARS-CoV-2-Antigen-Schnelltestgerät',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Hangzhou Genesis Biodetection & Biocontrol Co., Ltd.',
          name: 'KaiBiLi COVID-19 Antigen Pro',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Hangzhou Immuno Biotech Co.,Ltd.',
          name: 'IMMUNOBIO SARS-CoV-2 Antigen-Schnelltest (COVID-19 Ag)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Hangzhou Jucheng Medical Products Co., Ltd',
          name: 'SARS-CoV-2 Ag Schnelltestkit',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Hangzhou Laihe Biotech Co., Ltd. (Lissner Qi GmbH)',
          name: 'Lyher Novel Coronavirus (COVID-19) Antigen Test Kit (Colloidal Gold)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Hangzhou Lysun Biotechnology Co., Ltd.',
          name: 'Lysun COVID-19 Antigen Rapid Test Device (Colloidal Gold)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Hangzhou Sejoy Electronics & Instruments Co.,Ltd.',
          name: 'SARS-CoV-2 Antigen Schnelltestkassette',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Hangzhou Testsea Biotechnology Co., Ltd',
          name: 'Testsealabs® Rapid Test Kit COVID-19 Antigen Test Cassette',
          'omicron-sensitive': true,
        },
        {
          manufacturer:
            'Hangzhou Zheda Dixun Biological Gene Engineering Co., Ltd.',
          name: 'SARS-Cov-2 Nucleocapsid(N) Antigen Rapid Test Cassette',
          'omicron-sensitive': true,
        },
        {
          manufacturer:
            'Hangzhou Zheda Dixun Biological Gene Engineering Co., Ltd.',
          name: 'Bisdeal SARS-CoV-2 Antigen-Schnelltest',
          'omicron-sensitive': true,
        },
        {
          manufacturer:
            'Healgen Scientific Limited Liability Company (Siemens Healthineers)',
          name: 'CLINITEST® Rapid COVID-19 Antigen Test',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Hoyotek Biomedical Co., Ltd.',
          name: 'Corona Virus (COVID-19) Antigen Rapid Test (Colloidal Gold)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Hubei Jinjian Biology Co.,Ltd.',
          name: 'SARS-CoV-2 Antigen Test Kit (Colloidal Gold Method)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Humasis Co., Ltd.',
          name: 'Humasis COVID-19 Ag Test',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Innova Medical Group,Inc.',
          name: 'INNOVA SARS-CoV-2 Selbsttest (Qualitativer-Antigen-Schnelltest)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Innovation Biotech (Beijing) Co. LTD',
          name: 'INVBIO One Step Diagnostic Rapid Test Cassette',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Innovation Biotech (Beijing) Co.,Ltd',
          name: 'INVBIO Antigen Rapid Test Device (Saliva)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Innovita (Tangshan) Biological Technology Co.; LTD.',
          name: '2019-nCoV Ag Test (Latex Chromatography Assay)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'InTec Products, Inc.',
          name: 'Rapid SARS-CoV-2 Antigen Test Colloidal Gold (Nasopharyngeal/Nasal specimen)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Jiangsu Bioperfectus Technologies Co., Ltd.',
          name: 'Novel Coronavirus (SARS-CoV-2) Ag Rapid Test Kit',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Jiangsu Diagnostics Biotechnology Co., Ltd',
          name: 'COVID-19 Antigen Rapid Test Cassette (Colloidal Gold)',
          'omicron-sensitive': true,
        },
        {
          manufacturer:
            'Jiangsu Konsung Bio-Medical Science And Technology Co., Ltd',
          name: 'Konsung COVID-19 Antigen Rapid Test Kit',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Jiangsu Medomics Medical Technology Co., Ltd',
          name: 'SARS-CoV-2-Antigen-Testkit (LFIA)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Jiangsu Mole Bioscience Co., Ltd',
          name: 'SARS-CoV-2 Antigen Test Cassette',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Jiangsu Well Biotech Co., Ltd.',
          name: 'COVID-19 Schnelltestgerät',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Jiangxi Province JinHuan Medical Instrument Co.,LTD.',
          name: 'COVID-19 antigen Schnelltest (Kolloidales Gold) / Novel Coronavirus(SARS-CoV-2) Antigen Rapid Detection Kit',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Jiaxing Wisetest Bio-Tech Co., Ltd.',
          name: 'Saliva SARS-CoV-2 (2019-nCoV) Antigen Test Kit (Nanocarbon Assay)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Jinan Babio Biotechnology Co., Ltd.',
          name: 'SARS-CoV-2 Antigen Rapid Detection Kit (Colloidal Gold Method)',
          'omicron-sensitive': true,
        },
        {
          manufacturer:
            'Joinstar Biomedical Technology Co., Ltd (CIV care impuls Vertrieb)',
          name: 'COVID-19 Antigen Schnelltest (Colloidal Gold)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'JOYSBIO (Tianjin) Biotechnology Co., Ltd.',
          name: 'SARS-CoV-2 Antigen Rapid Test Kit (Colloidal Gold) SPUCKTEST',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'JOYSBIO (Tianjin) Biotechnology Co.,Ltd.',
          name: 'Joysbio SARS-CoV-2 Antigen rapid test kit -PRO (Colloidal Gold)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Labnovation Technologies, Inc.',
          name: 'Labnovation SARS-CoV-2 Antigen Rapid Test Kit (Immunochromatography)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Lifecosm Biotech Limited',
          name: 'COVID-19 Rapid Test Cassette Antigen Test Kit',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Lumigenex (Suzhou) Co., Ltd.',
          name: 'PocRoc SARS-CoV-2, Antigen Schnelltest Set (Kolloidales Gold)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'LumiQuick Diagnostics, Inc.',
          name: 'Quick Profile Covid-19 Antigen Test Card',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'LumiraDX',
          name: 'LumiraDx SARS-CoV-2 Ag Test',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'MEDsan GmbH',
          name: 'MEDsan® SARS-CoV-2 Antigen Rapid Test',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Merlin Biomedical (Xiamen) Co., Ltd.',
          name: 'SARS-CoV-2 Antigen Rapid Test Cassette',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Mölab GmbH',
          name: 'mö-screen Corona Antigen Test',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'MP Biomedicals Germany GmbH',
          name: 'Rapid SARS-CoV-2 Antigen Test Card',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'MSP bodmann GmbH',
          name: 'MSP SARS-CoV-2 Antigen-Schnelltest',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'nal von minden gmbh',
          name: 'NADAL® COVID-19 Ag Schnelltest',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Nanjing Liming Bio-Products Co., Ltd.',
          name: 'StrongStep® SARS-COV2 Antigen Rapid Test',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Nanjing Norman Biological Technology Co., Ltd',
          name: 'Novel Coronavirus (2019-nCOV) Antigen Testing Kit (Colloidal Gold)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Nanjing Synthgene Medical Technology Co., Ltd.',
          name: 'Synthgene Neues Coronavirus (SARS-CoV-2) Antigen-Schnellerkennungskit (Collate Gold-Methode)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Nanjing Vazyme Medical Technology Co., Ltd.',
          name: 'Vazyme SARS-CoV-2 Antigen Detection Kit (Colloidal Gold- Based)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'NanoEntek Inc',
          name: 'FRENDTM COVID-19 Ag',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Nantong Diagnos Biotechnology Co., Ltd.',
          name: 'COVID-19 Antigen Saliva Test Kit (Colloidal Gold)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Nantong Egens Biotechnology',
          name: 'SARS-CoV-2 Antigen Rapid Test',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Neo-nostics (Suzhou) Bioengeneering Co., Ltd.',
          name: 'COVID 19 Antigen Test Kit (Colloidal Gold Method)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'New Gene (Hangzhou) Bioengineering Co., Ltd.',
          name: 'Covid-19-Antigen-Testkit',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Ningbo Beautiful Life Medical Biotechnology',
          name: 'Saliva SARS-CoV-2(2019-nCoV) Antigen Test Kit (Nanocarbon Assay)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Novatech Tibbi Cihaz Ürünleri San. Ve Tic.A.S.',
          name: 'novacheck®-Ag SARS-CoV-2 Covid-19 Antigen Rapid Test',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Oncosem Onkolojik Sistemler San. Ve Tic.A.S.',
          name: 'CAT Antigen Covid Rapid Test',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'PCL, Inc.',
          name: 'PCL COVID19 Ag Gold Saliva',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'PerGrande BioTech Development Co., Ltd.',
          name: 'SARS-CoV-2 Antigen Detection Kit (Colloidal Gold Immunochromatographic Assay)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Precision Biosensor Inc. (Axon Lab AG)',
          name: 'Exdia COVID-19-Ag-Test',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'ProGnosis Biotech',
          name: 'Rapid Test Ag 2019-nCoV',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Pro-med (Beijing) Technology Co.,Ltd.',
          name: 'Pro-med COVID-19 Antigen Rapid Detection Kit',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Qingdao AIBO Diagnostic CO., Ltd.',
          name: 'Novel Coronavirus (COVID-19) Antigen Rapid Test Kit',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Qingdao Hightop Biotech Co., Ltd.',
          name: 'Hightop SARS-CoV-2 (Covid-19) Antigen Rapid Test',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'R-Biopharm AG',
          name: 'RIDA®QUICK SARS-CoV-2 Antigen',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Safecare Biotech Hangzhou Co., Ltd.',
          name: 'Safecare COVID-19 Ag Rapid Test Kit (Swab)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Salofa OY',
          name: 'salocor SARS-CoV-2 Antigen Rapid Test Cassette (Nasopharyngeal swab)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Sansure Biotech Inc.',
          name: 'SARS-CoV-2 Rapid Antigen Test (Colloidal Gold Method)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'ScheBo Biotech AG',
          name: 'ScheBo SARS-CoV-2 Quick Antigen',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'SD Biosensor, Inc.(Roche Diagnostics GmbH)',
          name: 'STANDARD Q COVID-19 Ag Test (SARS-CoV-2 Rapid Antigen Test)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'SD Biosensor, Inc.',
          name: 'STANDARD F COVID-19 Ag FIA',
          'omicron-sensitive': true,
        },
        {
          manufacturer:
            'Senova Gesellschaft für Biowissenschaft und Technik mbH',
          name: 'GreenLight SARS-CoV-2 Antigen-Test',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'SGA Mühendislik DAN. EG. Icve DIS.Ltd.STI',
          name: 'V-Chek SARS-CoV-2 Rapid Ag Test Kit (Colloidal Gold)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Shanghai Liangrun Biomedicine Technology Co., Ltd.',
          name: 'LionRunTM SARS-CoV-2 Antigen Rapid Test Kit (Lateral Flow Immunoassay)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Shen Zhen Zi Jian Biotechnology Co., Ltd.',
          name: 'Zijian SARS-CoV-2 (COVID-19) Antigen Rapid Detection Kit (Lateral Flow Method)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Shenzhen CAS-Envision Medical Technology Co., Ltd.',
          name: 'SARS-Cov-2 Antigen Rapid Detection Kit',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Shenzhen Dymind Biotechnology Co., Ltd.',
          name: 'SARS-CoV-2 Antigen Test Kit (Colloidal Gold)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Shenzhen Huaree Technology Co., Ltd.',
          name: 'SARS-CoV-2 Antigen Saliva Rapid Test Kit',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Shenzhen Huaree Technology Co.,Ltd.',
          name: 'SARS-CoV-2 Antigen Rapid Test Kit (Immunochromatography)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Shenzhen Huian Biosci Technology Co., Ltd.',
          name: 'SARS-CoV-2Antigen Test Kit (Colloidal Gold)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Shenzhen Kang Sheng Bao Bio- Technology Co., Ltd.',
          name: 'SARS-CoV-2 Antigen Rapid Test (Lateral Flow Assay)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Shenzhen Kingfocus Biomedical Engineering Co., Ltd.',
          name: 'COVID-19 Antigen Detection Kit (Quantum Dots-Based Immunofluorescence Chromatography)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Shenzhen Kisshealth Biotechnology Co., Ltd.',
          name: 'KISSH SARS-CoV-2 Antigen Test Kit (GICA)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Shenzhen Lvshiyuan Biotechnology Co., Ltd.',
          name: 'Green Spring SARS-CoV-2 Antigen Rapid Test Kit (Colloidal Gold)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Shenzhen Microprofit Biotech Co., Ltd.',
          name: 'fluorecare COVID-19 SARS-CoV-2 Spike Protein Test Kit (Colloidal Gold Chromatographic Immunoassay)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Shenzhen Microprofit Biotech Co., Ltd.',
          name: 'SARS-CoV-2 Spike Protein Test Kit (Fluorescence Immunoassay)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Shenzhen Microprofit Biotech Co., Ltd.',
          name: 'fluorecare SARS-CoV-2 Antigen Test Kit',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Shenzhen Reagent Technology Co., Ltd.',
          name: 'SARS-CoV-2 Antigen IVD kit SWAB',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Shenzhen Watmind Medical Co., Ltd.',
          name: 'SARS-CoV-2 Ag Diagnostic Test Kit (Colloidal Gold)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Shenzhen Watmind Medical Co., Ltd.',
          name: 'SARS-CoV-2 Ag Diagnostic Test Kit (Immunofluorescence)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Shenzhen YHLO Biotech Co., Ltd.',
          name: 'GLINE-2019-nCoV Ag',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Shenzhen Zhenrui Biotech Co., Ltd.',
          name: 'Zhenrui COVID-19 (SARS-COV-2) Antigen Test Kits',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Sichuan Xincheng Biological Co., Ltd.',
          name: 'SARS-CoV-2 Antigen Assay Kit by Latex Immunochromatography method',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Sugentech, Inc.',
          name: 'SGTi-flex COVID-19 Ag',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'SureScreen Diagnostics Ltd.',
          name: 'COVID-19 Antigen Rapid Test Cassette (Nasal Swab)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Surge Medical Inc.',
          name: 'COVID-19 Antigen Test Kit',
          'omicron-sensitive': true,
        },
        {
          manufacturer:
            'Suzhou Soochow University Saier Immuno Biotech Co., Ltd.',
          name: 'InstantSure Covid-19 Ag CARD',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'TBG Biotechnology Xiamen Inc.',
          name: 'TBG SARS-CoV-2 Antigen Rapid Test',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Toda Pharma',
          name: 'Toda Coronadiag Ag',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Triplex International Biosciences (China) Co., Ltd.',
          name: 'SARS-CoV-2 Antigen Rapid Test Kit',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Türklab Tibbi Malzemeleri San. Ve Tic. A.S',
          name: 'Rapidan Tester COVID-19 Ag Test',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'ulti med Products (Deutschland) GmbH',
          name: 'COVID-19 Antigen Speicheltest (Immunochromatographie)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Vitrosens Biyoteknoloji Ltd. Sti',
          name: 'RapidFor SARS-CoV-2 Rapid Antigen Test Colloidal Gold',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Weihai Kangzhou Biotechnology Engineering Co., Ltd.',
          name: 'Kanzone COVID-19 Antigen Rapid Test',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Wuhan EasyDiagnosis Biomedicine Co., Ltd.',
          name: 'COVID-19 (SARS-CoV-2) Antigen Test Kit',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Wuhan HealthCare Biotechnology Co., Ltd.',
          name: 'SARS-CoV-2 Antigen Test Kit (Colloidal Gold)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Wuhan Life Origin Biotech Joint Stock Co., Ltd.',
          name: 'SARS-CoV-2 Antigen Assay Kit (Immunochromatography)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Wuhan UNscience Biotechnology Co., Ltd.',
          name: 'SARS-CoV-2 Antigen Rapid Test Kit',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Wuxi Biohermes Bio & Medical Technology Co., Ltd.',
          name: 'SARS-CoV-2 Antigen Test Kit (Lateral Flow Assay)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Xiamen AmonMed Biotechnology Co., Ltd.',
          name: 'COVID-19 Antigen Rapid Test Kit (Colloidal Gold)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Xiamen Boson Biotech Co., Ltd.',
          name: 'SARS-CoV-2 Antigen Schnelltest',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Xiamen WIZ Biotech Co., Ltd.',
          name: 'Wizbiotech SARS-CoV-2 Antigen Rapid Test',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'ZandCell AB',
          name: 'ZandCell COVID-19 Saliva Antigen-Test',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Zet Medikal Tekstil Dis Ticaret Ltd. STI.',
          name: 'softec SARS COV-2 (Covid-19) Antigen Test Kit',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Zhejiang Anji Saianfu Biotech Co.,Ltd.',
          name: 'reOpenTest COVID-19 Antigen Rapid Test (Colloidal Gold)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Zhejiang Gene Science Co., Ltd.',
          name: 'Novel Coronavirus (COVID-19) Antigen Detection Kit (Latex Immunochromatography)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Zhejiang Orient Gene Biotech Co.,Ltd',
          name: 'Coronavirus Ag Rapid Test Cassette (Swab)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Zhongxiu Science and Technology Co., Ltd',
          name: 'Neuartiges Coronavirus (2019-nCoV) Antigendetektions¬reagenz (immunochromatographischer Assay)',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Zhuhai Encode Medical Engineering Co., Ltd.',
          name: 'ENCODE SARS-COV-2 Antigen Rapid Test Device',
          'omicron-sensitive': true,
        },
        {
          manufacturer: 'Zhuhai Lituo Biotechnology Co., Ltd.',
          name: 'COVID-19 Antigen Detection Kit (Colloidal Gold)',
          'omicron-sensitive': true,
        },
      ].sort((a, b) => {
        if (a['name'] <= b['name']) {
          return -1
        }
        return 1
      }),
      matchedSchnelltests: this.schnelltests,
    }
  },
  computed: {
    validSchnelltests() {
      if (!this.matchedSchnelltests) return 0
      return this.matchedSchnelltests.filter((a) => a['omicron-sensitive'])
        .length
    },
    invalidSchnelltests() {
      if (!this.matchedSchnelltests) return 0
      return this.matchedSchnelltests.filter((a) => !a['omicron-sensitive'])
        .length
    },
  },
  watch: {
    search(searchString) {
      if (!searchString) {
        this.matchedSchnelltests = this.schnelltests
      } else {
        const lowercaseSearchString = searchString.toLowerCase()

        this.matchedSchnelltests = this.schnelltests.filter(
          (test) =>
            test.name.toLowerCase().includes(lowercaseSearchString) ||
            test.manufacturer.toLowerCase().includes(lowercaseSearchString)
        )
      }
    },
  },
}
</script>

<style>
.v-list-item.primary--text.v-list-item--active.v-list-item--link {
  background: inherit;
  color: white !important;
  background: black;
}

.v-autocomplete__content {
  display: none !important;
}

.v-input__slot {
  padding-top: 20px !important;
  padding-bottom: 25px !important;
}
</style>
