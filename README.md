This guide is an attempt to demystify the suite of API's provided by the National Oceanic and Atmospheric Administration's (NOAA's) National Centers for Environmental Information (NCEI), which are rather sparsely documented.

First, request a token at this URL: https://www.ncdc.noaa.gov/cdo-web/token
Don't be alarmed by the NCDC URL. The National Climactic Data Center (NCDC) is the former name of the NCEI.

# NCEI Data Service API - https://www.ncei.noaa.gov/support/access-data-service-api-user-documentation

Use this API to get weather data.

**GET** `https://www.ncei.noaa.gov/access/services/data/v1?{paramKey1}={val1}&{paramKey2}={val2}`

|Parameter Key|Possible Values|Our Description|NCEI Description|
|---|---|---|---|
|dataset|daily-summaries, global-marine, global-summary-of-the-year||The dataset parameter selects the dataset to query for data. Please note that all the datasets are NOT available through the NCEI Access Data Service API, however new datasets are added quarterly.|
|stations|USC00457180, USC00390043, AUCE, ASN00084027||The stations parameter adds a comma separated list of station identifiers for selection and subsetting.|
|startDate|1776-07-04, 1941-12-07, 2001-11-02T12:45:00Z, 2001-11-02T12:45:00z, 2001-11-02T08:45:00+04:00||This is the date to select from the dataset for a given start date. This parameter is an ISO 8601 date (YYYY-MM-DD) -or- ISO 8601 combined date and time format (YYYY-MM-DDTHH:mm:ss). If using an ISO 8601 combined date and time format the T that separates the time is NOT optional. The ISO 8601 combined date and time also supports optional time zone representations.  Use Z or z for UTC and +HH:mm or -HH:mm for the offset from UTC. The plus symbol (+) must be URL encoded at “%2B” or it will not validate. The start and end dates are not required. The startDate must come before the endDate parameter. Some datasets are averages over time and may ignore parts of a date.|
|endDate|1776-07-04, 1941-12-07, 2001-11-02T12:45:00Z, 2001-11-02T12:45:00z, 2001-11-02T08:45:00+04:00||This is the date to select datasets whose period of record (PoR) starts on or after the given endDate. This parameter is an ISO 8601 date (YYYY-MM-DD) -or- ISO 8601 combined date and time format (YYYY-MM-DDTHH:mm:ss). If using an ISO 8601 combined date and time format, the T that separates the time is NOT optional. The ISO 8601 combined date and time also supports optional time zone representations.  Use Z or z for UTC and +HH:mm or -HH:mm for the offset from UTC. The plus symbol (+) must be URL encoded as “%2B” or it will not validate.  If the start date is required for the dataset then you must include the startDate parameter.|
|dataTypes|[ACCESS_STATUS_IND_ERR](https://github.com/partytax/ncei-api-guide#user-content-access_status_ind_err), [ACCESS_STATUS_IND_IVAD](https://github.com/partytax/ncei-api-guide#user-content-access_status_ind_ivad), [ADAPTIVE_QC_FLAGS](https://github.com/partytax/ncei-api-guide#user-content-adaptive_qc_flags), [AF-TRIM_FLAG](https://github.com/partytax/ncei-api-guide#user-content-af-trim_flag), [AH-HI_CLD_AMT_ECR](https://github.com/partytax/ncei-api-guide#user-content-ah-hi_cld_amt_ecr), [AIR_TEMP](https://github.com/partytax/ncei-api-guide#user-content-air_temp), [AM-MID_CLD_AMT_ECR](https://github.com/partytax/ncei-api-guide#user-content-am-mid_cld_amt_ecr), [AMT_PRECIP](https://github.com/partytax/ncei-api-guide#user-content-amt_precip), [AMT_PRES_TEND](https://github.com/partytax/ncei-api-guide#user-content-amt_pres_tend), [ANC-NCDC_QC_FLAGS](https://github.com/partytax/ncei-api-guide#user-content-anc-ncdc_qc_flags), [AQA-ADAPTIVE_QC_FLAGS](https://github.com/partytax/ncei-api-guide#user-content-aqa-adaptive_qc_flags), [AQZ-ADAPTIVE_QC_FLAGS](https://github.com/partytax/ncei-api-guide#user-content-aqz-adaptive_qc_flags), [ATTI-ATTM_IND5](https://github.com/partytax/ncei-api-guide#user-content-atti-attm_ind5), [ATTI-ATTM_IND6](https://github.com/partytax/ncei-api-guide#user-content-atti-attm_ind6), [ATTL-ATTM_LEN5](https://github.com/partytax/ncei-api-guide#user-content-attl-attm_len5), [ATTL-ATTM_LEN6](https://github.com/partytax/ncei-api-guide#user-content-attl-attm_len6), [ATTM_CT](https://github.com/partytax/ncei-api-guide#user-content-attm_ct), [ATTM_ENC](https://github.com/partytax/ncei-api-guide#user-content-attm_enc), [ATTM_ID](https://github.com/partytax/ncei-api-guide#user-content-attm_id), [ATTM_ID2](https://github.com/partytax/ncei-api-guide#user-content-attm_id2), [ATTM_ID3](https://github.com/partytax/ncei-api-guide#user-content-attm_id3), [ATTM_IND10](https://github.com/partytax/ncei-api-guide#user-content-attm_ind10), [ATTM_IND4](https://github.com/partytax/ncei-api-guide#user-content-attm_ind4), [ATTM_IND7](https://github.com/partytax/ncei-api-guide#user-content-attm_ind7), [ATTM_IND8](https://github.com/partytax/ncei-api-guide#user-content-attm_ind8), [ATTM_IND9](https://github.com/partytax/ncei-api-guide#user-content-attm_ind9), [ATTM_LEN](https://github.com/partytax/ncei-api-guide#user-content-attm_len), [ATTM_LEN10](https://github.com/partytax/ncei-api-guide#user-content-attm_len10), [ATTM_LEN2](https://github.com/partytax/ncei-api-guide#user-content-attm_len2), [ATTM_LEN3](https://github.com/partytax/ncei-api-guide#user-content-attm_len3), [ATTM_LEN4](https://github.com/partytax/ncei-api-guide#user-content-attm_len4), [ATTM_LEN7](https://github.com/partytax/ncei-api-guide#user-content-attm_len7), [ATTM_LEN8](https://github.com/partytax/ncei-api-guide#user-content-attm_len8), [ATTM_LEN9](https://github.com/partytax/ncei-api-guide#user-content-attm_len9), [AUTH_REF_CODE_ERR](https://github.com/partytax/ncei-api-guide#user-content-auth_ref_code_err), [AUTH_REF_CODE_IVAD](https://github.com/partytax/ncei-api-guide#user-content-auth_ref_code_ivad), [AWSI-AWS_IND](https://github.com/partytax/ncei-api-guide#user-content-awsi-aws_ind), [BD](https://github.com/partytax/ncei-api-guide#user-content-bd), [BFL](https://github.com/partytax/ncei-api-guide#user-content-bfl), [BH](https://github.com/partytax/ncei-api-guide#user-content-bh), [BM](https://github.com/partytax/ncei-api-guide#user-content-bm), [BMP](https://github.com/partytax/ncei-api-guide#user-content-bmp), [BNC-NCDC_QC_FLAGS](https://github.com/partytax/ncei-api-guide#user-content-bnc-ncdc_qc_flags), [BOX_SY_IND](https://github.com/partytax/ncei-api-guide#user-content-box_sy_ind), [BSAT](https://github.com/partytax/ncei-api-guide#user-content-bsat), [BSRH](https://github.com/partytax/ncei-api-guide#user-content-bsrh), [BSST](https://github.com/partytax/ncei-api-guide#user-content-bsst), [BSWU](https://github.com/partytax/ncei-api-guide#user-content-bswu), [BSWV](https://github.com/partytax/ncei-api-guide#user-content-bswv), [BUID](https://github.com/partytax/ncei-api-guide#user-content-buid), [BY1](https://github.com/partytax/ncei-api-guide#user-content-by1), [C1M-RECRUIT_COUNTRY](https://github.com/partytax/ncei-api-guide#user-content-c1m-recruit_country), [CCCC](https://github.com/partytax/ncei-api-guide#user-content-cccc), [CCE-CHANGE_CODE](https://github.com/partytax/ncei-api-guide#user-content-cce-change_code), [CHAR_PPP](https://github.com/partytax/ncei-api-guide#user-content-char_ppp), [CHE-HI_CLD_TYPE_ECR](https://github.com/partytax/ncei-api-guide#user-content-che-hi_cld_type_ecr), [CLD_HGT](https://github.com/partytax/ncei-api-guide#user-content-cld_hgt), [CLE-LOW_CLD_TYPE_ECR](https://github.com/partytax/ncei-api-guide#user-content-cle-low_cld_type_ecr), [CME-MID_CLD_TYPE_ECR](https://github.com/partytax/ncei-api-guide#user-content-cme-mid_cld_type_ecr), [CNC-NCDC_QC_FLAGS](https://github.com/partytax/ncei-api-guide#user-content-cnc-ncdc_qc_flags), [CONCEN_OF_SEA_ICE](https://github.com/partytax/ncei-api-guide#user-content-concen_of_sea_ice), [COR-COUNTRY_OF_REGISTER](https://github.com/partytax/ncei-api-guide#user-content-cor-country_of_register), [CORR_ERROR_FLAG](https://github.com/partytax/ncei-api-guide#user-content-corr_error_flag), [CORR_ERROR_VALUE](https://github.com/partytax/ncei-api-guide#user-content-corr_error_value), [COUNTRY_CODE](https://github.com/partytax/ncei-api-guide#user-content-country_code), [COURSE_OVER_GROUND](https://github.com/partytax/ncei-api-guide#user-content-course_over_ground), [CO_CODE_II](https://github.com/partytax/ncei-api-guide#user-content-co_code_ii), [CREATE_DAY_NUM_ERR](https://github.com/partytax/ncei-api-guide#user-content-create_day_num_err), [CREATE_DAY_NUM_IVAD](https://github.com/partytax/ncei-api-guide#user-content-create_day_num_ivad), [DECK](https://github.com/partytax/ncei-api-guide#user-content-deck), [DEP_LOAD_IN](https://github.com/partytax/ncei-api-guide#user-content-dep_load_in), [DEW_PT_TEMP](https://github.com/partytax/ncei-api-guide#user-content-dew_pt_temp), [DIR_OF_SWELL2](https://github.com/partytax/ncei-api-guide#user-content-dir_of_swell2), [DNC-NCDC_QC_FLAGS](https://github.com/partytax/ncei-api-guide#user-content-dnc-ncdc_qc_flags), [DOS-SST_DEPTH](https://github.com/partytax/ncei-api-guide#user-content-dos-sst_depth), [DPT_IND](https://github.com/partytax/ncei-api-guide#user-content-dpt_ind), [DQA-ADAPTIVE_QC_FLAGS](https://github.com/partytax/ncei-api-guide#user-content-dqa-adaptive_qc_flags), [DQZ-ADAPTIVE_QC_FLAGS](https://github.com/partytax/ncei-api-guide#user-content-dqz-adaptive_qc_flags), [DUP_CHK](https://github.com/partytax/ncei-api-guide#user-content-dup_chk), [DUP_STATUS](https://github.com/partytax/ncei-api-guide#user-content-dup_status), [DUR_OF_PER](https://github.com/partytax/ncei-api-guide#user-content-dur_of_per), [ENC-NCDC_QC_FLAGS](https://github.com/partytax/ncei-api-guide#user-content-enc-ncdc_qc_flags), [EOH-HYGRO_EXPOSURE](https://github.com/partytax/ncei-api-guide#user-content-eoh-hygro_exposure), [EOT-THERM_EXPOSURE](https://github.com/partytax/ncei-api-guide#user-content-eot-therm_exposure), [EXTERNAL](https://github.com/partytax/ncei-api-guide#user-content-external), [FBSRC](https://github.com/partytax/ncei-api-guide#user-content-fbsrc), [FIELD_NUM](https://github.com/partytax/ncei-api-guide#user-content-field_num), [FIELD_NUM_ERR](https://github.com/partytax/ncei-api-guide#user-content-field_num_err), [FM_CODE_VER](https://github.com/partytax/ncei-api-guide#user-content-fm_code_ver), [FNC-NCDC_QC_FLAGS](https://github.com/partytax/ncei-api-guide#user-content-fnc-ncdc_qc_flags), [GNC-NCDC_QC_FLAGS](https://github.com/partytax/ncei-api-guide#user-content-gnc-ncdc_qc_flags), [HE-LOW_CLD_HGT_ECR](https://github.com/partytax/ncei-api-guide#user-content-he-low_cld_hgt_ecr), [HGT_IND](https://github.com/partytax/ncei-api-guide#user-content-hgt_ind), [HGT_OF_SWELL2](https://github.com/partytax/ncei-api-guide#user-content-hgt_of_swell2), [HI_CLD_TYPE](https://github.com/partytax/ncei-api-guide#user-content-hi_cld_type), [HOA-HGT_ANEMOMETER](https://github.com/partytax/ncei-api-guide#user-content-hoa-hgt_anemometer), [HOB-HGT_BAR](https://github.com/partytax/ncei-api-guide#user-content-hob-hgt_bar), [HOP-HGT_VISUAL_OBS_PLATFORM](https://github.com/partytax/ncei-api-guide#user-content-hop-hgt_visual_obs_platform), [HOT-HGT_AT_SENSOR](https://github.com/partytax/ncei-api-guide#user-content-hot-hgt_at_sensor), [ICE_ACCR_ON_SHIP](https://github.com/partytax/ncei-api-guide#user-content-ice_accr_on_ship), [ICE_OF_LAND_ORIGIN](https://github.com/partytax/ncei-api-guide#user-content-ice_of_land_origin), [ICE_SIT_TREND](https://github.com/partytax/ncei-api-guide#user-content-ice_sit_trend), [ID_IND](https://github.com/partytax/ncei-api-guide#user-content-id_ind), [IMMA_VER](https://github.com/partytax/ncei-api-guide#user-content-imma_ver), [IMMT_VER](https://github.com/partytax/ncei-api-guide#user-content-immt_ver), [IMONO-IMO_NUM](https://github.com/partytax/ncei-api-guide#user-content-imono-imo_num), [IND_FOR_PRECIP](https://github.com/partytax/ncei-api-guide#user-content-ind_for_precip), [IND_FOR_TEMP](https://github.com/partytax/ncei-api-guide#user-content-ind_for_temp), [IND_FOR_WAVE_MEAS](https://github.com/partytax/ncei-api-guide#user-content-ind_for_wave_meas), [IND_FOR_WBT](https://github.com/partytax/ncei-api-guide#user-content-ind_for_wbt), [INPUT_COMP_NUM](https://github.com/partytax/ncei-api-guide#user-content-input_comp_num), [INPUT_COMP_NUM_ERR](https://github.com/partytax/ncei-api-guide#user-content-input_comp_num_err), [INTERMEDIATE_REJECT_FLAG](https://github.com/partytax/ncei-api-guide#user-content-intermediate_reject_flag), [KOV-KIND_OF_VESSEL](https://github.com/partytax/ncei-api-guide#user-content-kov-kind_of_vessel), [LANDLOCKED_FLAG](https://github.com/partytax/ncei-api-guide#user-content-landlocked_flag), [LL_IND](https://github.com/partytax/ncei-api-guide#user-content-ll_ind), [LOT-SCREEN_LOCATION](https://github.com/partytax/ncei-api-guide#user-content-lot-screen_location), [LOV-VESSEL_LENGTH](https://github.com/partytax/ncei-api-guide#user-content-lov-vessel_length), [LOW_CLD_AMT](https://github.com/partytax/ncei-api-guide#user-content-low_cld_amt), [LOW_CLD_TYPE](https://github.com/partytax/ncei-api-guide#user-content-low_cld_type), [MAX_HT_SUM_LOAD](https://github.com/partytax/ncei-api-guide#user-content-max_ht_sum_load), [META_SRC](https://github.com/partytax/ncei-api-guide#user-content-meta_src), [MID_CLD_TYPE](https://github.com/partytax/ncei-api-guide#user-content-mid_cld_type), [MQCS_VER](https://github.com/partytax/ncei-api-guide#user-content-mqcs_ver), [MSH](https://github.com/partytax/ncei-api-guide#user-content-msh), [MST](https://github.com/partytax/ncei-api-guide#user-content-mst), [NATIONAL_USE](https://github.com/partytax/ncei-api-guide#user-content-national_use), [NAT_SOURCE_IND](https://github.com/partytax/ncei-api-guide#user-content-nat_source_ind), [NCDC_QC_FLAGS](https://github.com/partytax/ncei-api-guide#user-content-ncdc_qc_flags), [NE-TTL_CLD_AMT_ECR](https://github.com/partytax/ncei-api-guide#user-content-ne-ttl_cld_amt_ecr), [NHE-LOW_CLD_AMT_ECR](https://github.com/partytax/ncei-api-guide#user-content-nhe-low_cld_amt_ecr), [NIGHT_DAY_FLAG](https://github.com/partytax/ncei-api-guide#user-content-night_day_flag), [NOL_HIGH_AMT_ECR](https://github.com/partytax/ncei-api-guide#user-content-nol_high_amt_ecr), [NOL_MID_AMT_ECR](https://github.com/partytax/ncei-api-guide#user-content-nol_mid_amt_ecr), [OAV-ALKALINITY](https://github.com/partytax/ncei-api-guide#user-content-oav-alkalinity), [OAZ-ALKALINITY_DEPTH](https://github.com/partytax/ncei-api-guide#user-content-oaz-alkalinity_depth), [OB_PLATFORM](https://github.com/partytax/ncei-api-guide#user-content-ob_platform), [OB_SOURCE](https://github.com/partytax/ncei-api-guide#user-content-ob_source), [OCV-TTL_CHLORO](https://github.com/partytax/ncei-api-guide#user-content-ocv-ttl_chloro), [OCZ-TTL_CHLORO_DEPTH](https://github.com/partytax/ncei-api-guide#user-content-ocz-ttl_chloro_depth), [ODV-DIS_ORG_CARBON](https://github.com/partytax/ncei-api-guide#user-content-odv-dis_org_carbon), [ODZ-DIS_ORG_CARBON_DEPTH](https://github.com/partytax/ncei-api-guide#user-content-odz-dis_org_carbon_depth), [ONE_BOX_NUM](https://github.com/partytax/ncei-api-guide#user-content-one_box_num), [ONV-NITRATE](https://github.com/partytax/ncei-api-guide#user-content-onv-nitrate), [ONZ-NITRATE_DEPTH](https://github.com/partytax/ncei-api-guide#user-content-onz-nitrate_depth), [OOV-DIS_OXYGEN](https://github.com/partytax/ncei-api-guide#user-content-oov-dis_oxygen), [OOZ-DIS_OXYGEN_DEPTH](https://github.com/partytax/ncei-api-guide#user-content-ooz-dis_oxygen_depth), [OPCV-PP_CO2](https://github.com/partytax/ncei-api-guide#user-content-opcv-pp_co2), [OPCZ-PP_CO2_DEPTH](https://github.com/partytax/ncei-api-guide#user-content-opcz-pp_co2_depth), [OPHV-PH](https://github.com/partytax/ncei-api-guide#user-content-ophv-ph), [OPHZ-PH_DEPTH](https://github.com/partytax/ncei-api-guide#user-content-ophz-ph_depth), [OPM-SHIP_TYPE](https://github.com/partytax/ncei-api-guide#user-content-opm-ship_type), [OPV-PHOSPHATE](https://github.com/partytax/ncei-api-guide#user-content-opv-phosphate), [OPZ-PHOSPHATE_DEPTH](https://github.com/partytax/ncei-api-guide#user-content-opz-phosphate_depth), [OSIV-SILICATE](https://github.com/partytax/ncei-api-guide#user-content-osiv-silicate), [OSIZ-SILICATE_DEPTH](https://github.com/partytax/ncei-api-guide#user-content-osiz-silicate_depth), [OSV-SALINITY](https://github.com/partytax/ncei-api-guide#user-content-osv-salinity), [OSZ-SALINITY_DEPTH](https://github.com/partytax/ncei-api-guide#user-content-osz-salinity_depth), [OTV-SST2](https://github.com/partytax/ncei-api-guide#user-content-otv-sst2), [OTZ-SST_DEPTH2](https://github.com/partytax/ncei-api-guide#user-content-otz-sst_depth2), [PAST_WX](https://github.com/partytax/ncei-api-guide#user-content-past_wx), [PAST_WX2](https://github.com/partytax/ncei-api-guide#user-content-past_wx2), [PER_OF_SWELL2](https://github.com/partytax/ncei-api-guide#user-content-per_of_swell2), [PF-TRIM_FLAG](https://github.com/partytax/ncei-api-guide#user-content-pf-trim_flag), [PLATFORM_ID](https://github.com/partytax/ncei-api-guide#user-content-platform_id), [PNC-NCDC_QC_FLAGS](https://github.com/partytax/ncei-api-guide#user-content-pnc-ncdc_qc_flags), [PQA-ADAPTIVE_QC_FLAGS](https://github.com/partytax/ncei-api-guide#user-content-pqa-adaptive_qc_flags), [PQZ-ADAPTIVE_QC_FLAGS](https://github.com/partytax/ncei-api-guide#user-content-pqz-adaptive_qc_flags), [PRESS_BIAS](https://github.com/partytax/ncei-api-guide#user-content-press_bias), [PRES_WX](https://github.com/partytax/ncei-api-guide#user-content-pres_wx), [PUID-PROVIDER_UID](https://github.com/partytax/ncei-api-guide#user-content-puid-provider_uid), [QC_IND](https://github.com/partytax/ncei-api-guide#user-content-qc_ind), [QC_IND_FOR_FIELDS](https://github.com/partytax/ncei-api-guide#user-content-qc_ind_for_fields), [QI1-QC_IND_FOR_FIELDS](https://github.com/partytax/ncei-api-guide#user-content-qi1-qc_ind_for_fields), [QI10-QC_IND_FOR_FIELDS](https://github.com/partytax/ncei-api-guide#user-content-qi10-qc_ind_for_fields), [QI11-QC_IND_FOR_FIELDS](https://github.com/partytax/ncei-api-guide#user-content-qi11-qc_ind_for_fields), [QI12-QC_IND_FOR_FIELDS](https://github.com/partytax/ncei-api-guide#user-content-qi12-qc_ind_for_fields), [QI13-QC_IND_FOR_FIELDS](https://github.com/partytax/ncei-api-guide#user-content-qi13-qc_ind_for_fields), [QI14-QC_IND_FOR_FIELDS](https://github.com/partytax/ncei-api-guide#user-content-qi14-qc_ind_for_fields), [QI15-QC_IND_FOR_FIELDS](https://github.com/partytax/ncei-api-guide#user-content-qi15-qc_ind_for_fields), [QI16-QC_IND_FOR_FIELDS](https://github.com/partytax/ncei-api-guide#user-content-qi16-qc_ind_for_fields), [QI17-QC_IND_FOR_FIELDS](https://github.com/partytax/ncei-api-guide#user-content-qi17-qc_ind_for_fields), [QI18-QC_IND_FOR_FIELDS](https://github.com/partytax/ncei-api-guide#user-content-qi18-qc_ind_for_fields), [QI19-QC_IND_FOR_FIELDS](https://github.com/partytax/ncei-api-guide#user-content-qi19-qc_ind_for_fields), [QI2-QC_IND_FOR_FIELDS](https://github.com/partytax/ncei-api-guide#user-content-qi2-qc_ind_for_fields), [QI20-QC_IND_FOR_FIELDS](https://github.com/partytax/ncei-api-guide#user-content-qi20-qc_ind_for_fields), [QI22-IMMT_QC_SHIP_HEADING](https://github.com/partytax/ncei-api-guide#user-content-qi22-immt_qc_ship_heading), [QI23-IMMT_QC_COURSE_OVER_GROUND](https://github.com/partytax/ncei-api-guide#user-content-qi23-immt_qc_course_over_ground), [QI24-IMMT_QC_SHIP_SPEED_OVER_GROUND](https://github.com/partytax/ncei-api-guide#user-content-qi24-immt_qc_ship_speed_over_ground), [QI25-IMMT_QC_MAX_HT_SUM_LOAD](https://github.com/partytax/ncei-api-guide#user-content-qi25-immt_qc_max_ht_sum_load), [QI27-IMMT_QC_DEP_SUM_LOAD](https://github.com/partytax/ncei-api-guide#user-content-qi27-immt_qc_dep_sum_load), [QI28-IMMT_QC_REL_WIND_DIR](https://github.com/partytax/ncei-api-guide#user-content-qi28-immt_qc_rel_wind_dir), [QI29-IMMT_QC_REL_WIND_SPEED](https://github.com/partytax/ncei-api-guide#user-content-qi29-immt_qc_rel_wind_speed), [QI3-QC_IND_FOR_FIELDS](https://github.com/partytax/ncei-api-guide#user-content-qi3-qc_ind_for_fields), [QI4-QC_IND_FOR_FIELDS](https://github.com/partytax/ncei-api-guide#user-content-qi4-qc_ind_for_fields), [QI5-QC_IND_FOR_FIELDS](https://github.com/partytax/ncei-api-guide#user-content-qi5-qc_ind_for_fields), [QI6-QC_IND_FOR_FIELDS](https://github.com/partytax/ncei-api-guide#user-content-qi6-qc_ind_for_fields), [QI7-QC_IND_FOR_FIELDS](https://github.com/partytax/ncei-api-guide#user-content-qi7-qc_ind_for_fields), [QI8-QC_IND_FOR_FIELDS](https://github.com/partytax/ncei-api-guide#user-content-qi8-qc_ind_for_fields), [QI9-QC_IND_FOR_FIELDS](https://github.com/partytax/ncei-api-guide#user-content-qi9-qc_ind_for_fields), [RATE_OF_I](https://github.com/partytax/ncei-api-guide#user-content-rate_of_i), [RELEASE_NUM_PRIMARY](https://github.com/partytax/ncei-api-guide#user-content-release_num_primary), [RELEASE_NUM_SECONDARY](https://github.com/partytax/ncei-api-guide#user-content-release_num_secondary), [RELEASE_NUM_TERTIARY](https://github.com/partytax/ncei-api-guide#user-content-release_num_tertiary), [RELEASE_STATUS_IND](https://github.com/partytax/ncei-api-guide#user-content-release_status_ind), [REL_LUNAR_ILLUM](https://github.com/partytax/ncei-api-guide#user-content-rel_lunar_illum), [REL_WIND_DIR](https://github.com/partytax/ncei-api-guide#user-content-rel_wind_dir), [REL_WIND_SPD](https://github.com/partytax/ncei-api-guide#user-content-rel_wind_spd), [RF-TRIM_FLAG](https://github.com/partytax/ncei-api-guide#user-content-rf-trim_flag), [RH](https://github.com/partytax/ncei-api-guide#user-content-rh), [RH_IND](https://github.com/partytax/ncei-api-guide#user-content-rh_ind), [SEA_LVL_PRES](https://github.com/partytax/ncei-api-guide#user-content-sea_lvl_pres), [SEA_SURF_TEMP](https://github.com/partytax/ncei-api-guide#user-content-sea_surf_temp), [SF-TRIM_FLAG](https://github.com/partytax/ncei-api-guide#user-content-sf-trim_flag), [SHIP_COURSE](https://github.com/partytax/ncei-api-guide#user-content-ship_course), [SHIP_HEADING](https://github.com/partytax/ncei-api-guide#user-content-ship_heading), [SHIP_ID](https://github.com/partytax/ncei-api-guide#user-content-ship_id), [SHIP_SPD](https://github.com/partytax/ncei-api-guide#user-content-ship_spd), [SIG_CLOUD_AMT](https://github.com/partytax/ncei-api-guide#user-content-sig_cloud_amt), [SIG_CLOUD_HGT](https://github.com/partytax/ncei-api-guide#user-content-sig_cloud_hgt), [SIG_CLOUD_TYPE](https://github.com/partytax/ncei-api-guide#user-content-sig_cloud_type), [SIM-SST_METHOD](https://github.com/partytax/ncei-api-guide#user-content-sim-sst_method), [SKY_BRIGHT_IND](https://github.com/partytax/ncei-api-guide#user-content-sky_bright_ind), [SME-SRC_META_ELEMENT](https://github.com/partytax/ncei-api-guide#user-content-sme-src_meta_element), [SMF-SRC_META_FILE](https://github.com/partytax/ncei-api-guide#user-content-smf-src_meta_file), [SMV-SRC_FORMAT_VER](https://github.com/partytax/ncei-api-guide#user-content-smv-src_format_ver), [SNC-NCDC_QC_FLAGS](https://github.com/partytax/ncei-api-guide#user-content-snc-ncdc_qc_flags), [SOLAR_ALT](https://github.com/partytax/ncei-api-guide#user-content-solar_alt), [SOURCE_EXCLUSION_FLAG](https://github.com/partytax/ncei-api-guide#user-content-source_exclusion_flag), [SOURCE_ID](https://github.com/partytax/ncei-api-guide#user-content-source_id), [SPD_OVER_GROUND](https://github.com/partytax/ncei-api-guide#user-content-spd_over_ground), [SQA-ADAPTIVE_QC_FLAGS](https://github.com/partytax/ncei-api-guide#user-content-sqa-adaptive_qc_flags), [SQZ-ADAPTIVE_QC_FLAGS](https://github.com/partytax/ncei-api-guide#user-content-sqz-adaptive_qc_flags), [SRH](https://github.com/partytax/ncei-api-guide#user-content-srh), [SST_MM](https://github.com/partytax/ncei-api-guide#user-content-sst_mm), [STAGE_OF_DEVELP](https://github.com/partytax/ncei-api-guide#user-content-stage_of_develp), [STA_WX_IND](https://github.com/partytax/ncei-api-guide#user-content-sta_wx_ind), [SUPPLEMENTAL_DATA](https://github.com/partytax/ncei-api-guide#user-content-supplemental_data), [SWELL_DIR](https://github.com/partytax/ncei-api-guide#user-content-swell_dir), [SWELL_HGT](https://github.com/partytax/ncei-api-guide#user-content-swell_hgt), [SWELL_PERIOD](https://github.com/partytax/ncei-api-guide#user-content-swell_period), [SWELL_PERIOD_IND](https://github.com/partytax/ncei-api-guide#user-content-swell_period_ind), [SWU](https://github.com/partytax/ncei-api-guide#user-content-swu), [SWV](https://github.com/partytax/ncei-api-guide#user-content-swv), [TEN_BOX_NUM](https://github.com/partytax/ncei-api-guide#user-content-ten_box_num), [THICKNESS_OF_I](https://github.com/partytax/ncei-api-guide#user-content-thickness_of_i), [TIME_IND](https://github.com/partytax/ncei-api-guide#user-content-time_ind), [TNC-NCDC_QC_FLAGS](https://github.com/partytax/ncei-api-guide#user-content-tnc-ncdc_qc_flags), [TOB-BAR_TYPE](https://github.com/partytax/ncei-api-guide#user-content-tob-bar_type), [TOH-HYGRO_TYPE](https://github.com/partytax/ncei-api-guide#user-content-toh-hygro_type), [TOT-THERM_TYPE](https://github.com/partytax/ncei-api-guide#user-content-tot-therm_type), [TOT_CLD_AMT](https://github.com/partytax/ncei-api-guide#user-content-tot_cld_amt), [TRACK_CHK](https://github.com/partytax/ncei-api-guide#user-content-track_chk), [TRIM_FLAG](https://github.com/partytax/ncei-api-guide#user-content-trim_flag), [TRUE_BEARING_ICE_EDGE](https://github.com/partytax/ncei-api-guide#user-content-true_bearing_ice_edge), [TYPE_IND_VAU1](https://github.com/partytax/ncei-api-guide#user-content-type_ind_vau1), [TYPE_IND_VAU2](https://github.com/partytax/ncei-api-guide#user-content-type_ind_vau2), [TYPE_IND_VAU3](https://github.com/partytax/ncei-api-guide#user-content-type_ind_vau3), [UF-TRIM_FLAG](https://github.com/partytax/ncei-api-guide#user-content-uf-trim_flag), [UNCERT_TYPE_IVAU1](https://github.com/partytax/ncei-api-guide#user-content-uncert_type_ivau1), [UNCERT_TYPE_IVAU2](https://github.com/partytax/ncei-api-guide#user-content-uncert_type_ivau2), [UNCERT_TYPE_IVAU3](https://github.com/partytax/ncei-api-guide#user-content-uncert_type_ivau3), [UNIQUE_ID](https://github.com/partytax/ncei-api-guide#user-content-unique_id), [UQA-ADAPTIVE_QC_FLAGS](https://github.com/partytax/ncei-api-guide#user-content-uqa-adaptive_qc_flags), [UQZ-ADAPTIVE_QC_FLAGS](https://github.com/partytax/ncei-api-guide#user-content-uqz-adaptive_qc_flags), [VAD_QC](https://github.com/partytax/ncei-api-guide#user-content-vad_qc), [VAD_SCALE_FACTOR](https://github.com/partytax/ncei-api-guide#user-content-vad_scale_factor), [VALUE_ADDED](https://github.com/partytax/ncei-api-guide#user-content-value_added), [VAU1_SCALE_FACTOR](https://github.com/partytax/ncei-api-guide#user-content-vau1_scale_factor), [VAU2_SCALE_FACTOR](https://github.com/partytax/ncei-api-guide#user-content-vau2_scale_factor), [VAU3_SCALE_FACTOR](https://github.com/partytax/ncei-api-guide#user-content-vau3_scale_factor), [VF-TRIM_FLAG](https://github.com/partytax/ncei-api-guide#user-content-vf-trim_flag), [VISIBILITY](https://github.com/partytax/ncei-api-guide#user-content-visibility), [VQA-ADAPTIVE_QC_FLAGS](https://github.com/partytax/ncei-api-guide#user-content-vqa-adaptive_qc_flags), [VQZ-ADAPTIVE_QC_FLAGS](https://github.com/partytax/ncei-api-guide#user-content-vqz-adaptive_qc_flags), [VV_IND](https://github.com/partytax/ncei-api-guide#user-content-vv_ind), [WAVE_DIR](https://github.com/partytax/ncei-api-guide#user-content-wave_dir), [WAVE_HGT](https://github.com/partytax/ncei-api-guide#user-content-wave_hgt), [WAVE_PERIOD](https://github.com/partytax/ncei-api-guide#user-content-wave_period), [WAVE_PERIOD_IND](https://github.com/partytax/ncei-api-guide#user-content-wave_period_ind), [WET_BULB_TEMP](https://github.com/partytax/ncei-api-guide#user-content-wet_bulb_temp), [WIND_DIR](https://github.com/partytax/ncei-api-guide#user-content-wind_dir), [WIND_DIR_IND](https://github.com/partytax/ncei-api-guide#user-content-wind_dir_ind), [WIND_SPD](https://github.com/partytax/ncei-api-guide#user-content-wind_spd), [WIND_SPD_IND](https://github.com/partytax/ncei-api-guide#user-content-wind_spd_ind), [WIND_SPEED](https://github.com/partytax/ncei-api-guide#user-content-wind_speed), [WNC-NCDC_QC_FLAGS](https://github.com/partytax/ncei-api-guide#user-content-wnc-ncdc_qc_flags), [WWE-PRES_WX_ECR](https://github.com/partytax/ncei-api-guide#user-content-wwe-pres_wx_ecr), [XNC-NCDC_QC_FLAGS](https://github.com/partytax/ncei-api-guide#user-content-xnc-ncdc_qc_flags), [YNC-NCDC_QC_FLAGS](https://github.com/partytax/ncei-api-guide#user-content-ync-ncdc_qc_flags), [ZNC-NCDC_QC_FLAGS](https://github.com/partytax/ncei-api-guide#user-content-znc-ncdc_qc_flags), [alt](https://github.com/partytax/ncei-api-guide#user-content-alt), [lat](https://github.com/partytax/ncei-api-guide#user-content-lat), [lon](https://github.com/partytax/ncei-api-guide#user-content-lon), [station_info](https://github.com/partytax/ncei-api-guide#user-content-station_info), [station_name](https://github.com/partytax/ncei-api-guide#user-content-station_name), [time](https://github.com/partytax/ncei-api-guide#user-content-time)||Data Types allows the selection of one or many dataTypes. Datasets have different names for the data types (e.g., variables, observations). The dataTypes parameter is used with a comma-separated list. This parameter is case-sensitive and will respond with an HTTPS Status Code: 400 Bad Request and JSON with more information.|
|boundingBox|49.795,-2.073,49.183,-0.992||The bounding box is used to select data from a geographic location contained within the coordinates, given as four comma separated numbers. North and South range from -90 to 90 and East and West range from -180 to 180. If these are not set the geographic extent defaults to the entire globe (90,-180,-90,180).|
|format|csv, ssv, json, pdf, netcdf (probably exhaustive)||The format parameter allows the user to select how the data should be formatted. Note that some data formats ignore certain data types. For example, PDF data may only display data types for a report, and not for the requested dataTypes.|
|options|includeAttributes:true,includeStationName:1 ||The API supports an options parameter that turns features on and off. Options are separated by commas and the respective values are separated by a colon (:); boolean values are represented by true or false,or zero (0) and one (1). Options can either pass as a comma-separated list: …&options=includeAttributes:true,includeStationName:1 or individually as URL parameters: ...&includeAttributes=0&includeStationName=true|
|includeAttributes|true, false||Includes the attribute for a selected datatype. These are typically comma separated (e.g., “T,,0,0700”), and added to the results if the includeAttributes parameter is set to true. This value can be the word true or a numeric representation of the boolean value, 1. The default value is false or 0 and will not display datatype(s) attributes.|
|includeStationName|true, false||Includes the station’s name, if available, for the selected dataset and data type. This value can be the word true or a numeric representation of the boolean value, 1. The default value is false or 0 and will not display datatype(s) attributes.|
|includeStationLocation|1, 0, true, false||Includes the station’s location, if available, for the selected dataset and data type. This value can be the word true or a numeric representation of the boolean value, 1. The default value is false or 0 and will not display datatype(s) attributes.|
|units|metric, standard||The units parameter converts the output data for datasets and datatypes that support conversion to either “metric” or “standard” units.|

## Detailed Value Descriptions
### dataTypes

|Value|NCEI Description|
|---|---|
|<span id='ACCESS_STATUS_IND_ERR'>ACCESS_STATUS_IND_ERR</span>|Access Status Indicator - Error|
|<span id='ACCESS_STATUS_IND_IVAD'>ACCESS_STATUS_IND_IVAD</span>|Access Status Indicator|
|<span id='ADAPTIVE_QC_FLAGS'>ADAPTIVE_QC_FLAGS</span>|ADAPTIVE_QC_FLAGS|
|<span id='AF-TRIM_FLAG'>AF-TRIM_FLAG</span>|Trimming Flag - Air Temperature|
|<span id='AH-HI_CLD_AMT_ECR'>AH-HI_CLD_AMT_ECR</span>|Extended Cloud Reconstructions High Cloud Amount|
|<span id='AIR_TEMP'>AIR_TEMP</span>|Air Temperature|
|<span id='AM-MID_CLD_AMT_ECR'>AM-MID_CLD_AMT_ECR</span>|Extended Cloud Reconstructions Middle Cloud Amount|
|<span id='AMT_PRECIP'>AMT_PRECIP</span>|Precipitation Amount|
|<span id='AMT_PRES_TEND'>AMT_PRES_TEND</span>|Pressure Tendency|
|<span id='ANC-NCDC_QC_FLAGS'>ANC-NCDC_QC_FLAGS</span>|NCDC QC Flags - Air Temp|
|<span id='AQA-ADAPTIVE_QC_FLAGS'>AQA-ADAPTIVE_QC_FLAGS</span>|Adaptive QC Flag - Air Temperature|
|<span id='AQZ-ADAPTIVE_QC_FLAGS'>AQZ-ADAPTIVE_QC_FLAGS</span>|Adaptive QC Flag - Air Temperature|
|<span id='ATTI-ATTM_IND5'>ATTI-ATTM_IND5</span>|Attachment Indicator 5|
|<span id='ATTI-ATTM_IND6'>ATTI-ATTM_IND6</span>|Attachment Indicator 6|
|<span id='ATTL-ATTM_LEN5'>ATTL-ATTM_LEN5</span>|Attachment Length 5|
|<span id='ATTL-ATTM_LEN6'>ATTL-ATTM_LEN6</span>|Attachment Length 6|
|<span id='ATTM_CT'>ATTM_CT</span>|Attachment Count|
|<span id='ATTM_ENC'>ATTM_ENC</span>|Attachment Encoding|
|<span id='ATTM_ID'>ATTM_ID</span>|Attachment Indicator|
|<span id='ATTM_ID2'>ATTM_ID2</span>|Attachment Indicator 2|
|<span id='ATTM_ID3'>ATTM_ID3</span>|Attachment Indicator 3|
|<span id='ATTM_IND10'>ATTM_IND10</span>|Attachment Indicator 10|
|<span id='ATTM_IND4'>ATTM_IND4</span>|Attachment Indicator 4|
|<span id='ATTM_IND7'>ATTM_IND7</span>|Attachment Indicator 7|
|<span id='ATTM_IND8'>ATTM_IND8</span>|Attachment Indicator 8|
|<span id='ATTM_IND9'>ATTM_IND9</span>|Attachment Indicator 9|
|<span id='ATTM_LEN'>ATTM_LEN</span>|Attachment Length|
|<span id='ATTM_LEN10'>ATTM_LEN10</span>|Attachment Length 10|
|<span id='ATTM_LEN2'>ATTM_LEN2</span>|Attachment Length 2|
|<span id='ATTM_LEN3'>ATTM_LEN3</span>|Attachment Length 3|
|<span id='ATTM_LEN4'>ATTM_LEN4</span>|Attachment Length 4|
|<span id='ATTM_LEN7'>ATTM_LEN7</span>|Attachment Length 7|
|<span id='ATTM_LEN8'>ATTM_LEN8</span>|Attachment Length 8|
|<span id='ATTM_LEN9'>ATTM_LEN9</span>|Attachment Length 9|
|<span id='AUTH_REF_CODE_ERR'>AUTH_REF_CODE_ERR</span>|Author Reference Code - Error|
|<span id='AUTH_REF_CODE_IVAD'>AUTH_REF_CODE_IVAD</span>|Author Reference Code|
|<span id='AWSI-AWS_IND'>AWSI-AWS_IND</span>|Automatic Weather Station Indicator|
|<span id='BD'>BD</span>|Background Day|
|<span id='BFL'>BFL</span>|Time Period Displacement|
|<span id='BH'>BH</span>|Background Hour|
|<span id='BM'>BM</span>|Background Month|
|<span id='BMP'>BMP</span>|Background Sea Level Pressure|
|<span id='BNC-NCDC_QC_FLAGS'>BNC-NCDC_QC_FLAGS</span>|NCDC QC Flags - Visibility|
|<span id='BOX_SY_IND'>BOX_SY_IND</span>|Box System Indicator|
|<span id='BSAT'>BSAT</span>|Background Air Temperature|
|<span id='BSRH'>BSRH</span>|Background Relative Humidity|
|<span id='BSST'>BSST</span>|Background SST|
|<span id='BSWU'>BSWU</span>|Background Wind U Component|
|<span id='BSWV'>BSWV</span>|Background Wind V Component|
|<span id='BUID'>BUID</span>|Bulletin ID|
|<span id='BY1'>BY1</span>|Background Year|
|<span id='C1M-RECRUIT_COUNTRY'>C1M-RECRUIT_COUNTRY</span>|Recruiting Country|
|<span id='CCCC'>CCCC</span>|Collecting Center|
|<span id='CCE-CHANGE_CODE'>CCE-CHANGE_CODE</span>|Change Code|
|<span id='CHAR_PPP'>CHAR_PPP</span>|Characteristics of Pressure Tendency|
|<span id='CHE-HI_CLD_TYPE_ECR'>CHE-HI_CLD_TYPE_ECR</span>|Extended Cloud Reconstructions High Cloud Type|
|<span id='CLD_HGT'>CLD_HGT</span>|Cloud Height|
|<span id='CLE-LOW_CLD_TYPE_ECR'>CLE-LOW_CLD_TYPE_ECR</span>|Extended Cloud Reconstructions Low Cloud Type|
|<span id='CME-MID_CLD_TYPE_ECR'>CME-MID_CLD_TYPE_ECR</span>|Extended Cloud Reconstructions Middle Cloud Type|
|<span id='CNC-NCDC_QC_FLAGS'>CNC-NCDC_QC_FLAGS</span>|NCDC QC Flags - Clouds|
|<span id='CONCEN_OF_SEA_ICE'>CONCEN_OF_SEA_ICE</span>|Concentration of Sea Ice|
|<span id='COR-COUNTRY_OF_REGISTER'>COR-COUNTRY_OF_REGISTER</span>|Country of Register|
|<span id='CORR_ERROR_FLAG'>CORR_ERROR_FLAG</span>|Corrected/Erroneous Field Flag|
|<span id='CORR_ERROR_VALUE'>CORR_ERROR_VALUE</span>|Corrected/Erroneous Field Value|
|<span id='COUNTRY_CODE'>COUNTRY_CODE</span>|Country Code|
|<span id='COURSE_OVER_GROUND'>COURSE_OVER_GROUND</span>|Ship's Course Over Ground|
|<span id='CO_CODE_II'>CO_CODE_II</span>|Country Code 2|
|<span id='CREATE_DAY_NUM_ERR'>CREATE_DAY_NUM_ERR</span>|Creation Day Number - Error|
|<span id='CREATE_DAY_NUM_IVAD'>CREATE_DAY_NUM_IVAD</span>|Creation Day Number|
|<span id='DECK'>DECK</span>|Deck|
|<span id='DEP_LOAD_IN'>DEP_LOAD_IN</span>|Departure from Maximum Height of Cargo Above Max Summer Load Line|
|<span id='DEW_PT_TEMP'>DEW_PT_TEMP</span>|Dew Point Temperature|
|<span id='DIR_OF_SWELL2'>DIR_OF_SWELL2</span>|Swell Direction 2|
|<span id='DNC-NCDC_QC_FLAGS'>DNC-NCDC_QC_FLAGS</span>|NCDC QC Flags - Dew Point|
|<span id='DOS-SST_DEPTH'>DOS-SST_DEPTH</span>|SST Depth|
|<span id='DPT_IND'>DPT_IND</span>|Dew Point Temperature Indicator|
|<span id='DQA-ADAPTIVE_QC_FLAGS'>DQA-ADAPTIVE_QC_FLAGS</span>|Adaptive QC Flag - Dew Point Temperature|
|<span id='DQZ-ADAPTIVE_QC_FLAGS'>DQZ-ADAPTIVE_QC_FLAGS</span>|Adaptive QC Flag - Dew Point Temperature|
|<span id='DUP_CHK'>DUP_CHK</span>|Duplicate Check|
|<span id='DUP_STATUS'>DUP_STATUS</span>|Duplicate Status|
|<span id='DUR_OF_PER'>DUR_OF_PER</span>|Duration of Precipitation|
|<span id='ENC-NCDC_QC_FLAGS'>ENC-NCDC_QC_FLAGS</span>|NCDC QC Flags - Wind Waves|
|<span id='EOH-HYGRO_EXPOSURE'>EOH-HYGRO_EXPOSURE</span>|Hygrometer Exposure|
|<span id='EOT-THERM_EXPOSURE'>EOT-THERM_EXPOSURE</span>|Thermometer Exposure|
|<span id='EXTERNAL'>EXTERNAL</span>|Externally Provided QC Flags|
|<span id='FBSRC'>FBSRC</span>|Feedback Source|
|<span id='FIELD_NUM'>FIELD_NUM</span>|Field Number|
|<span id='FIELD_NUM_ERR'>FIELD_NUM_ERR</span>|Field Number - Error|
|<span id='FM_CODE_VER'>FM_CODE_VER</span>|FM SHIP Code Version|
|<span id='FNC-NCDC_QC_FLAGS'>FNC-NCDC_QC_FLAGS</span>|NCDC QC Flags - Swells|
|<span id='GNC-NCDC_QC_FLAGS'>GNC-NCDC_QC_FLAGS</span>|NCDC QC Flags - Wet Bulb|
|<span id='HE-LOW_CLD_HGT_ECR'>HE-LOW_CLD_HGT_ECR</span>|Extended Cloud Reconstructions Low Cloud Height|
|<span id='HGT_IND'>HGT_IND</span>|Cloud Height Indicator|
|<span id='HGT_OF_SWELL2'>HGT_OF_SWELL2</span>|Swell Height 2|
|<span id='HI_CLD_TYPE'>HI_CLD_TYPE</span>|High Cloud Type|
|<span id='HOA-HGT_ANEMOMETER'>HOA-HGT_ANEMOMETER</span>|Height of Anemometer|
|<span id='HOB-HGT_BAR'>HOB-HGT_BAR</span>|Height of Barometer|
|<span id='HOP-HGT_VISUAL_OBS_PLATFORM'>HOP-HGT_VISUAL_OBS_PLATFORM</span>|Height of Visual Observation Platform|
|<span id='HOT-HGT_AT_SENSOR'>HOT-HGT_AT_SENSOR</span>|Height of Air Temperature Sensor|
|<span id='ICE_ACCR_ON_SHIP'>ICE_ACCR_ON_SHIP</span>|Ice Accretion On Ship|
|<span id='ICE_OF_LAND_ORIGIN'>ICE_OF_LAND_ORIGIN</span>|Ice of Land Origin|
|<span id='ICE_SIT_TREND'>ICE_SIT_TREND</span>|Ice trend|
|<span id='ID_IND'>ID_IND</span>|Identification Indicator|
|<span id='IMMA_VER'>IMMA_VER</span>|IMMA Version|
|<span id='IMMT_VER'>IMMT_VER</span>|IMMT Version|
|<span id='IMONO-IMO_NUM'>IMONO-IMO_NUM</span>|IMO Number|
|<span id='IND_FOR_PRECIP'>IND_FOR_PRECIP</span>|Precipitation Indicator|
|<span id='IND_FOR_TEMP'>IND_FOR_TEMP</span>|Temperature Indicator|
|<span id='IND_FOR_WAVE_MEAS'>IND_FOR_WAVE_MEAS</span>|Wave Measurement Indicator|
|<span id='IND_FOR_WBT'>IND_FOR_WBT</span>|Wet Bulb Temperature Indicator|
|<span id='INPUT_COMP_NUM'>INPUT_COMP_NUM</span>|Input Component Number|
|<span id='INPUT_COMP_NUM_ERR'>INPUT_COMP_NUM_ERR</span>|Input Component Number - Error|
|<span id='INTERMEDIATE_REJECT_FLAG'>INTERMEDIATE_REJECT_FLAG</span>|Intermediate Reject Flag|
|<span id='KOV-KIND_OF_VESSEL'>KOV-KIND_OF_VESSEL</span>|Kind of Vessel|
|<span id='LANDLOCKED_FLAG'>LANDLOCKED_FLAG</span>|Landlocked Flag|
|<span id='LL_IND'>LL_IND</span>|Latitude Longitude Indicator|
|<span id='LOT-SCREEN_LOCATION'>LOT-SCREEN_LOCATION</span>|Screen Location|
|<span id='LOV-VESSEL_LENGTH'>LOV-VESSEL_LENGTH</span>|Vessel Length|
|<span id='LOW_CLD_AMT'>LOW_CLD_AMT</span>|Low Cloud Amount|
|<span id='LOW_CLD_TYPE'>LOW_CLD_TYPE</span>|Low Cloud Type|
|<span id='MAX_HT_SUM_LOAD'>MAX_HT_SUM_LOAD</span>|Maximum Height of Cargo Above Max Summer Load Line|
|<span id='META_SRC'>META_SRC</span>|Metadata Source|
|<span id='MID_CLD_TYPE'>MID_CLD_TYPE</span>|Middle Cloud Type|
|<span id='MQCS_VER'>MQCS_VER</span>|Version of Minimum QC Standards (MQCS)|
|<span id='MSH'>MSH</span>|Model Surface Height|
|<span id='MST'>MST</span>|Model Surface Type|
|<span id='NATIONAL_USE'>NATIONAL_USE</span>|National Use|
|<span id='NAT_SOURCE_IND'>NAT_SOURCE_IND</span>|National Source Indicator|
|<span id='NCDC_QC_FLAGS'>NCDC_QC_FLAGS</span>|NCDC_QC_FLAGS|
|<span id='NE-TTL_CLD_AMT_ECR'>NE-TTL_CLD_AMT_ECR</span>|Extended Cloud Reconstructions Total Cloud Amount|
|<span id='NHE-LOW_CLD_AMT_ECR'>NHE-LOW_CLD_AMT_ECR</span>|Extended Cloud Reconstructions Low Cloud Amount|
|<span id='NIGHT_DAY_FLAG'>NIGHT_DAY_FLAG</span>|Night/Day Flag|
|<span id='NOL_HIGH_AMT_ECR'>NOL_HIGH_AMT_ECR</span>|Extended Cloud Reconstructions NOL High Cloud Amount|
|<span id='NOL_MID_AMT_ECR'>NOL_MID_AMT_ECR</span>|Extended Cloud Reconstructions NOL Middle Cloud Amount|
|<span id='OAV-ALKALINITY'>OAV-ALKALINITY</span>|Alkalinity|
|<span id='OAZ-ALKALINITY_DEPTH'>OAZ-ALKALINITY_DEPTH</span>|Alkalinity Depth|
|<span id='OB_PLATFORM'>OB_PLATFORM</span>|Observation Platform|
|<span id='OB_SOURCE'>OB_SOURCE</span>|Observation Source|
|<span id='OCV-TTL_CHLORO'>OCV-TTL_CHLORO</span>|Total Chlorophyll|
|<span id='OCZ-TTL_CHLORO_DEPTH'>OCZ-TTL_CHLORO_DEPTH</span>|Total Chlorophyll Depth|
|<span id='ODV-DIS_ORG_CARBON'>ODV-DIS_ORG_CARBON</span>|Dissolved Organic Carbon|
|<span id='ODZ-DIS_ORG_CARBON_DEPTH'>ODZ-DIS_ORG_CARBON_DEPTH</span>|Dissolved Organic Carbon Depth|
|<span id='ONE_BOX_NUM'>ONE_BOX_NUM</span>|One Degree Box Number|
|<span id='ONV-NITRATE'>ONV-NITRATE</span>|Nitrate|
|<span id='ONZ-NITRATE_DEPTH'>ONZ-NITRATE_DEPTH</span>|Nitrate Depth|
|<span id='OOV-DIS_OXYGEN'>OOV-DIS_OXYGEN</span>|Dissolved Oxygen|
|<span id='OOZ-DIS_OXYGEN_DEPTH'>OOZ-DIS_OXYGEN_DEPTH</span>|Dissolved Oxygen Depth|
|<span id='OPCV-PP_CO2'>OPCV-PP_CO2</span>|Partial Pressure of Carbon Dioxide|
|<span id='OPCZ-PP_CO2_DEPTH'>OPCZ-PP_CO2_DEPTH</span>|Partial Pressure of Carbon Dioxide Depth|
|<span id='OPHV-PH'>OPHV-PH</span>|PH|
|<span id='OPHZ-PH_DEPTH'>OPHZ-PH_DEPTH</span>|PH Depth|
|<span id='OPM-SHIP_TYPE'>OPM-SHIP_TYPE</span>|Ship Type|
|<span id='OPV-PHOSPHATE'>OPV-PHOSPHATE</span>|Phosphate|
|<span id='OPZ-PHOSPHATE_DEPTH'>OPZ-PHOSPHATE_DEPTH</span>|Phosphate Depth|
|<span id='OSIV-SILICATE'>OSIV-SILICATE</span>|Silicate|
|<span id='OSIZ-SILICATE_DEPTH'>OSIZ-SILICATE_DEPTH</span>|Silicated Depth|
|<span id='OSV-SALINITY'>OSV-SALINITY</span>|Salinity|
|<span id='OSZ-SALINITY_DEPTH'>OSZ-SALINITY_DEPTH</span>|Salinity Depth|
|<span id='OTV-SST2'>OTV-SST2</span>|SST 2|
|<span id='OTZ-SST_DEPTH2'>OTZ-SST_DEPTH2</span>|SST Depth 2|
|<span id='PAST_WX'>PAST_WX</span>|Past Weather|
|<span id='PAST_WX2'>PAST_WX2</span>|Past Weather 2|
|<span id='PER_OF_SWELL2'>PER_OF_SWELL2</span>|Swell Period 2|
|<span id='PF-TRIM_FLAG'>PF-TRIM_FLAG</span>|Trimming Flag - Sea Level Pressure|
|<span id='PLATFORM_ID'>PLATFORM_ID</span>|Platform Type Indicator|
|<span id='PNC-NCDC_QC_FLAGS'>PNC-NCDC_QC_FLAGS</span>|NCDC QC Flags - SLP|
|<span id='PQA-ADAPTIVE_QC_FLAGS'>PQA-ADAPTIVE_QC_FLAGS</span>|Adaptive QC Flag - Sea Leve Pressure|
|<span id='PQZ-ADAPTIVE_QC_FLAGS'>PQZ-ADAPTIVE_QC_FLAGS</span>|Adaptive QC Flag - Sea Leve Pressure|
|<span id='PRESS_BIAS'>PRESS_BIAS</span>|Pressure Bias|
|<span id='PRES_WX'>PRES_WX</span>|Present Weather|
|<span id='PUID-PROVIDER_UID'>PUID-PROVIDER_UID</span>|Provider's Unique Record Identification|
|<span id='QC_IND'>QC_IND</span>|QC Indicator|
|<span id='QC_IND_FOR_FIELDS'>QC_IND_FOR_FIELDS</span>|QC_IND_FOR_FIELDS|
|<span id='QI1-QC_IND_FOR_FIELDS'>QI1-QC_IND_FOR_FIELDS</span>|QC Flag - height of clouds|
|<span id='QI10-QC_IND_FOR_FIELDS'>QI10-QC_IND_FOR_FIELDS</span>|QC Flag - sea surface temperature|
|<span id='QI11-QC_IND_FOR_FIELDS'>QI11-QC_IND_FOR_FIELDS</span>|QC Flag - period of wind waves|
|<span id='QI12-QC_IND_FOR_FIELDS'>QI12-QC_IND_FOR_FIELDS</span>|QC Flag - height of wind waves|
|<span id='QI13-QC_IND_FOR_FIELDS'>QI13-QC_IND_FOR_FIELDS</span>|QC Flag - swell|
|<span id='QI14-QC_IND_FOR_FIELDS'>QI14-QC_IND_FOR_FIELDS</span>|QC Flag - precipitation|
|<span id='QI15-QC_IND_FOR_FIELDS'>QI15-QC_IND_FOR_FIELDS</span>|QC Flag - characteristic of pressure tendency|
|<span id='QI16-QC_IND_FOR_FIELDS'>QI16-QC_IND_FOR_FIELDS</span>|QC Flag - amount of pressure tendency|
|<span id='QI17-QC_IND_FOR_FIELDS'>QI17-QC_IND_FOR_FIELDS</span>|QC Flag - true direction of ship|
|<span id='QI18-QC_IND_FOR_FIELDS'>QI18-QC_IND_FOR_FIELDS</span>|QC Flag - ship's average speed|
|<span id='QI19-QC_IND_FOR_FIELDS'>QI19-QC_IND_FOR_FIELDS</span>|QC Flag - wet bulb temperature|
|<span id='QI2-QC_IND_FOR_FIELDS'>QI2-QC_IND_FOR_FIELDS</span>|QC Flag - visibility|
|<span id='QI20-QC_IND_FOR_FIELDS'>QI20-QC_IND_FOR_FIELDS</span>|QC Flag - ship's position|
|<span id='QI22-IMMT_QC_SHIP_HEADING'>QI22-IMMT_QC_SHIP_HEADING</span>|QC Flag - ship's heading|
|<span id='QI23-IMMT_QC_COURSE_OVER_GROUND'>QI23-IMMT_QC_COURSE_OVER_GROUND</span>|QC Flag - ship's course over ground|
|<span id='QI24-IMMT_QC_SHIP_SPEED_OVER_GROUND'>QI24-IMMT_QC_SHIP_SPEED_OVER_GROUND</span>|QC Flag - ship's speed over ground|
|<span id='QI25-IMMT_QC_MAX_HT_SUM_LOAD'>QI25-IMMT_QC_MAX_HT_SUM_LOAD</span>|QC Flag - summer load line|
|<span id='QI27-IMMT_QC_DEP_SUM_LOAD'>QI27-IMMT_QC_DEP_SUM_LOAD</span>|QC Flag - departure from summer load line|
|<span id='QI28-IMMT_QC_REL_WIND_DIR'>QI28-IMMT_QC_REL_WIND_DIR</span>|QC Flag - relative wind direction|
|<span id='QI29-IMMT_QC_REL_WIND_SPEED'>QI29-IMMT_QC_REL_WIND_SPEED</span>|QC Flag - relative wind speed|
|<span id='QI3-QC_IND_FOR_FIELDS'>QI3-QC_IND_FOR_FIELDS</span>|QC Flag - clouds|
|<span id='QI4-QC_IND_FOR_FIELDS'>QI4-QC_IND_FOR_FIELDS</span>|QC Flag - wind direction|
|<span id='QI5-QC_IND_FOR_FIELDS'>QI5-QC_IND_FOR_FIELDS</span>|QC Flag - wind speed|
|<span id='QI6-QC_IND_FOR_FIELDS'>QI6-QC_IND_FOR_FIELDS</span>|QC Flag - air temperature|
|<span id='QI7-QC_IND_FOR_FIELDS'>QI7-QC_IND_FOR_FIELDS</span>|QC Flag - dew point temperature|
|<span id='QI8-QC_IND_FOR_FIELDS'>QI8-QC_IND_FOR_FIELDS</span>|QC Flag - air pressure|
|<span id='QI9-QC_IND_FOR_FIELDS'>QI9-QC_IND_FOR_FIELDS</span>|QC Flag - weather|
|<span id='RATE_OF_I'>RATE_OF_I</span>|Rate of Ice Accretion on Ship|
|<span id='RELEASE_NUM_PRIMARY'>RELEASE_NUM_PRIMARY</span>|Release Number Primary|
|<span id='RELEASE_NUM_SECONDARY'>RELEASE_NUM_SECONDARY</span>|Release Number Secondary|
|<span id='RELEASE_NUM_TERTIARY'>RELEASE_NUM_TERTIARY</span>|Release Number Tertiary|
|<span id='RELEASE_STATUS_IND'>RELEASE_STATUS_IND</span>|Release Status Indicator|
|<span id='REL_LUNAR_ILLUM'>REL_LUNAR_ILLUM</span>|Relative Lunar Illuminance|
|<span id='REL_WIND_DIR'>REL_WIND_DIR</span>|Relative Wind Direction|
|<span id='REL_WIND_SPD'>REL_WIND_SPD</span>|Relative Wind Speed|
|<span id='RF-TRIM_FLAG'>RF-TRIM_FLAG</span>|Trimming Flag - Relative Humidity|
|<span id='RH'>RH</span>|Relative Humidity|
|<span id='RH_IND'>RH_IND</span>|Relative Humidity Indicator|
|<span id='SEA_LVL_PRES'>SEA_LVL_PRES</span>|Sea Level Pressure|
|<span id='SEA_SURF_TEMP'>SEA_SURF_TEMP</span>|Sea Surface Temperature|
|<span id='SF-TRIM_FLAG'>SF-TRIM_FLAG</span>|Trimming Flag - SST|
|<span id='SHIP_COURSE'>SHIP_COURSE</span>|Ship's Course|
|<span id='SHIP_HEADING'>SHIP_HEADING</span>|Ship's Heading|
|<span id='SHIP_ID'>SHIP_ID</span>|Identification|
|<span id='SHIP_SPD'>SHIP_SPD</span>|Ship's Speed|
|<span id='SIG_CLOUD_AMT'>SIG_CLOUD_AMT</span>|Significant Cloud Amount|
|<span id='SIG_CLOUD_HGT'>SIG_CLOUD_HGT</span>|Significant Cloud Height|
|<span id='SIG_CLOUD_TYPE'>SIG_CLOUD_TYPE</span>|Significant Cloud Type|
|<span id='SIM-SST_METHOD'>SIM-SST_METHOD</span>|SST Method|
|<span id='SKY_BRIGHT_IND'>SKY_BRIGHT_IND</span>|Sky Brightness Indicator|
|<span id='SME-SRC_META_ELEMENT'>SME-SRC_META_ELEMENT</span>|Source Metadata Element|
|<span id='SMF-SRC_META_FILE'>SMF-SRC_META_FILE</span>|Source Metadata File|
|<span id='SMV-SRC_FORMAT_VER'>SMV-SRC_FORMAT_VER</span>|Source Metadata Format Version|
|<span id='SNC-NCDC_QC_FLAGS'>SNC-NCDC_QC_FLAGS</span>|NCDC QC Flags - SST|
|<span id='SOLAR_ALT'>SOLAR_ALT</span>|Solar Altitude|
|<span id='SOURCE_EXCLUSION_FLAG'>SOURCE_EXCLUSION_FLAG</span>|Source Exclusion Flag|
|<span id='SOURCE_ID'>SOURCE_ID</span>|Source|
|<span id='SPD_OVER_GROUND'>SPD_OVER_GROUND</span>|Ship's Speed Over Ground|
|<span id='SQA-ADAPTIVE_QC_FLAGS'>SQA-ADAPTIVE_QC_FLAGS</span>|Adaptive QC Flag - SST|
|<span id='SQZ-ADAPTIVE_QC_FLAGS'>SQZ-ADAPTIVE_QC_FLAGS</span>|Adaptive QC Flag - SST|
|<span id='SRH'>SRH</span>|Derived Relative Humidity|
|<span id='SST_MM'>SST_MM</span>|Sea Surface Temperature Method Indicator|
|<span id='STAGE_OF_DEVELP'>STAGE_OF_DEVELP</span>|Stage of Development of Sea Ice|
|<span id='STA_WX_IND'>STA_WX_IND</span>|Weather Indicator|
|<span id='SUPPLEMENTAL_DATA'>SUPPLEMENTAL_DATA</span>|Supplemental Data|
|<span id='SWELL_DIR'>SWELL_DIR</span>|Swell Direction|
|<span id='SWELL_HGT'>SWELL_HGT</span>|Swell Height|
|<span id='SWELL_PERIOD'>SWELL_PERIOD</span>|Swell Period|
|<span id='SWELL_PERIOD_IND'>SWELL_PERIOD_IND</span>|Swell Period Indicator|
|<span id='SWU'>SWU</span>|Derived Wind U Component|
|<span id='SWV'>SWV</span>|Derived Wind V Component|
|<span id='TEN_BOX_NUM'>TEN_BOX_NUM</span>|Ten Degree Box Number|
|<span id='THICKNESS_OF_I'>THICKNESS_OF_I</span>|Thickness of Ice Accretion On Ship|
|<span id='TIME_IND'>TIME_IND</span>|Time Indicator|
|<span id='TNC-NCDC_QC_FLAGS'>TNC-NCDC_QC_FLAGS</span>|NCDC QC Flags - Character of Pressure Tendency|
|<span id='TOB-BAR_TYPE'>TOB-BAR_TYPE</span>|Barometer Type|
|<span id='TOH-HYGRO_TYPE'>TOH-HYGRO_TYPE</span>|Hygrometer Type|
|<span id='TOT-THERM_TYPE'>TOT-THERM_TYPE</span>|Thermometer Type|
|<span id='TOT_CLD_AMT'>TOT_CLD_AMT</span>|Total Cloud Amount|
|<span id='TRACK_CHK'>TRACK_CHK</span>|Track Check|
|<span id='TRIM_FLAG'>TRIM_FLAG</span>|TRIM_FLAG|
|<span id='TRUE_BEARING_ICE_EDGE'>TRUE_BEARING_ICE_EDGE</span>|Ice Edge Bearing|
|<span id='TYPE_IND_VAU1'>TYPE_IND_VAU1</span>|Type Indicator for VAU1|
|<span id='TYPE_IND_VAU2'>TYPE_IND_VAU2</span>|Type Indicator for VAU2|
|<span id='TYPE_IND_VAU3'>TYPE_IND_VAU3</span>|Type Indicator for VAU3|
|<span id='UF-TRIM_FLAG'>UF-TRIM_FLAG</span>|Trimming Flag - U Wind Component|
|<span id='UNCERT_TYPE_IVAU1'>UNCERT_TYPE_IVAU1</span>|Uncertainty Type for VAU1|
|<span id='UNCERT_TYPE_IVAU2'>UNCERT_TYPE_IVAU2</span>|Uncertainty Type for VAU2|
|<span id='UNCERT_TYPE_IVAU3'>UNCERT_TYPE_IVAU3</span>|Uncertainty Type for VAU3|
|<span id='UNIQUE_ID'>UNIQUE_ID</span>|Unique Report ID|
|<span id='UQA-ADAPTIVE_QC_FLAGS'>UQA-ADAPTIVE_QC_FLAGS</span>|Adaptive QC Flag - U Wind Component|
|<span id='UQZ-ADAPTIVE_QC_FLAGS'>UQZ-ADAPTIVE_QC_FLAGS</span>|Adaptive QC Flag - U Wind Component|
|<span id='VAD_QC'>VAD_QC</span>|Value-Added Data QC Flag|
|<span id='VAD_SCALE_FACTOR'>VAD_SCALE_FACTOR</span>|Value-Added Data Scale Factor|
|<span id='VALUE_ADDED'>VALUE_ADDED</span>|Value-Added Data|
|<span id='VAU1_SCALE_FACTOR'>VAU1_SCALE_FACTOR</span>|Scaling Factor for VAU1|
|<span id='VAU2_SCALE_FACTOR'>VAU2_SCALE_FACTOR</span>|Scaling Factor for VAU2|
|<span id='VAU3_SCALE_FACTOR'>VAU3_SCALE_FACTOR</span>|Scaling Factor for VAU3|
|<span id='VF-TRIM_FLAG'>VF-TRIM_FLAG</span>|Trimming Flag - V Wind Component|
|<span id='VISIBILITY'>VISIBILITY</span>|Visibility|
|<span id='VQA-ADAPTIVE_QC_FLAGS'>VQA-ADAPTIVE_QC_FLAGS</span>|Adaptive QC Flag - V Wind Component|
|<span id='VQZ-ADAPTIVE_QC_FLAGS'>VQZ-ADAPTIVE_QC_FLAGS</span>|Adaptive QC Flag - V Wind Component|
|<span id='VV_IND'>VV_IND</span>|Visibility Indicator|
|<span id='WAVE_DIR'>WAVE_DIR</span>|Wave Direction|
|<span id='WAVE_HGT'>WAVE_HGT</span>|Wave Height|
|<span id='WAVE_PERIOD'>WAVE_PERIOD</span>|Wave Period|
|<span id='WAVE_PERIOD_IND'>WAVE_PERIOD_IND</span>|Wave Period Indicator|
|<span id='WET_BULB_TEMP'>WET_BULB_TEMP</span>|Wet Bulb Temperature|
|<span id='WIND_DIR'>WIND_DIR</span>|Wind Direction|
|<span id='WIND_DIR_IND'>WIND_DIR_IND</span>|Wind Direction Indicator|
|<span id='WIND_SPD'>WIND_SPD</span>|Wind Speed|
|<span id='WIND_SPD_IND'>WIND_SPD_IND</span>|Wind Speed Indicator|
|<span id='WIND_SPEED'>WIND_SPEED</span>|Wind Speed|
|<span id='WNC-NCDC_QC_FLAGS'>WNC-NCDC_QC_FLAGS</span>|NCDC QC Flags - Wind|
|<span id='WWE-PRES_WX_ECR'>WWE-PRES_WX_ECR</span>|Extended Cloud Reconstructions Present Weather|
|<span id='XNC-NCDC_QC_FLAGS'>XNC-NCDC_QC_FLAGS</span>|NCDC QC Flags - Present Wx|
|<span id='YNC-NCDC_QC_FLAGS'>YNC-NCDC_QC_FLAGS</span>|NCDC QC Flags - Past Wx|
|<span id='ZNC-NCDC_QC_FLAGS'>ZNC-NCDC_QC_FLAGS</span>|NCDC QC Flags - Full Report|
|<span id='alt'>alt</span>|the elevation of a geophysical point of observation relative to Mean Sea Level|
|<span id='lat'>lat</span>|GEOPHYSICAL-POINT-OBSERVATION latitude coordinate|
|<span id='lon'>lon</span>|GEOPHYSICAL-POINT-OBSERVATION longitude coordinate|
|<span id='station_info'>station_info</span>|name of the station|
|<span id='station_name'>station_name</span>|station identification code|
|<span id='time'>time</span>|time of observation|

# NCEI Support Service API - https://www.ncei.noaa.gov/support/access-support-service

Use this API to get information about what attributes are available for a given dataset.

**GET** `https://www.ncei.noaa.gov/access/services/support/v3/datasets/{datasetId}.json`

|Parameter Key|Possible Values|Our Description|NCEI Description|
|---|---|---|---|
|datasetId|daily-summaries, global-marine, global-summary-of-the-year||The National Centers for Environmental Information (NCEI) Common Access Support Service provides a RESTful application programming interface (API) to discover metadata and attributes about datasets based on a set of parameters to the /v3/datasets URL. |

Other NOAA weather/climate API's:
* Climate Data Online (CDO) - https://www.ncdc.noaa.gov/cdo-web/webservices/v2
