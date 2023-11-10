<script setup lang="ts">
import { ref, computed } from 'vue'
import { availableVersion, maintenanceVersion } from './version'
import type { MVersion, AVersion } from './version'

const mVersionSearch = ref<'Maintenance' | null>('Maintenance')
const mVersion: MVersion[] = maintenanceVersion
const mVersionCp = computed(() => {
  if (mVersionSearch.value) {
    return mVersion.filter((row) => row.maintaine === mVersionSearch.value)
  } else return mVersion
})
const mVersionToggle = () => {
  mVersionSearch.value = mVersionSearch.value ? null : 'Maintenance'
}

const aVersionSearch = ref<string | null>(null)
const aVersion: AVersion[] = availableVersion
const aVersionCP = computed(() => {
  if (aVersionSearch.value !== null) {
    // @ts-ignore
    return aVersion.filter((row) => row.patches.includes(aVersionSearch.value))
  } else return aVersion
})
</script>

<template>
  <div
    id="sap-ui-static"
    style="height: 0px; width: 0px; overflow: hidden; float: left"
    data-sap-ui-area="sap-ui-static"
  >
    <span id="sap-ui-static-firstfe" tabindex="-1" style="font-size: 0px"></span
    ><span
      id="__text1"
      data-sap-ui="__text1"
      class="sapUiInvisibleText"
      aria-hidden="true"
      >Schließen der Warnmeldungszeile</span
    ><span
      id="__text4"
      data-sap-ui="__text4"
      class="sapUiInvisibleText"
      aria-hidden="true"
      >Schließen der Informationsmeldungszeile</span
    ><span
      id="__text6"
      data-sap-ui="__text6"
      class="sapUiInvisibleText"
      aria-hidden="true"
      >Verfügbare Werte</span
    ><span
      id="__text15"
      data-sap-ui="__text15"
      class="sapUiInvisibleText"
      aria-hidden="true"
      >Schließen der Informationsmeldungszeile</span
    ><span
      id="__text18"
      data-sap-ui="__text18"
      class="sapUiInvisibleText"
      aria-hidden="true"
      >Suchfeld</span
    >
  </div>
  <div id="messages" class="messages" data-sap-ui-area="messages">
    <div
      id="__strip0"
      data-sap-ui="__strip0"
      data-sap-ui-render=""
      data-sap-ui-fastnavgroup="true"
      data-sap-ui-ms-closable="false"
      role="note"
      aria-labelledby="__strip0"
      aria-roledescription="Informationsleiste"
      class="sapMMsgStrip sapMMsgStripWarning"
    >
      <span id="__strip0-info" class="sapUiPseudoInvisibleText"
        >Nachrichtenzeile für Warnung</span
      >
      <div class="sapMMsgStripIcon">
        <span
          data-sap-ui-icon-content=""
          role="presentation"
          aria-hidden="true"
          id="id-1699627596546-11"
          aria-label="alert"
          class="sapUiIcon sapUiIconMirrorInRTL"
          style="font-family: 'SAP-icons'"
        ></span>
      </div>
      <div id="__strip0-content" class="sapMMsgStripMessage">
        <div
          id="__text2"
          data-sap-ui="__text2"
          data-sap-ui-render=""
          class="sapMFT"
          style=""
        >
          To ensure outdated versions are no longer posing a potential security
          risk, OpenUI5 versions will be removed from
          <a
            href="https://sdk.openui5.org/"
            target="_blank"
            rel="noopener noreferrer"
            class="sapMLnk"
            style="position: static !important"
            >OpenUI5 CDN</a
          >
          one year after their end of maintenance. In addition, also patches of
          versions in maintenance older than one year will be removed. Details
          see in
          <a
            href="https://blogs.sap.com/2021/01/26/removing-outdated-ui5-versions-from-ui5-cdn/"
            target="_blank"
            rel="noopener noreferrer"
            class="sapMLnk"
            style="position: static !important"
            >Blog post</a
          >. It's recommended to always upgrade to the latest version in order
          to get the latest fixes and improvements!
          <a
            href="/topic/2d3eb2f322ea4a82983c1c62a33ec4ae"
            target="_blank"
            rel="noopener noreferrer"
            class="sapMLnk"
            style="position: static !important"
            >Read more...</a
          >
        </div>
      </div>
    </div>
    <div
      id="__strip1"
      data-sap-ui="__strip1"
      data-sap-ui-render=""
      data-sap-ui-fastnavgroup="true"
      data-sap-ui-ms-closable="true"
      role="note"
      aria-labelledby="__strip1"
      aria-roledescription="Informationsleiste"
      class="sapMMsgStrip sapMMsgStripInformation"
    >
      <span id="__strip1-info" class="sapUiPseudoInvisibleText"
        >Nachrichtenzeile für Informationen Schließbar</span
      >
      <div class="sapMMsgStripIcon">
        <span
          data-sap-ui-icon-content=""
          role="presentation"
          aria-hidden="true"
          id="id-1699627596548-12"
          aria-label="information"
          class="sapUiIcon sapUiIconMirrorInRTL"
          style="font-family: 'SAP-icons'"
        ></span>
      </div>
      <div id="__strip1-content" class="sapMMsgStripMessage">
        <div
          id="__text5"
          data-sap-ui="__text5"
          data-sap-ui-render=""
          class="sapMFT"
          style=""
        >
          Security-related information to OpenUI5 consumption:
          <ul style="position: static !important">
            <li style="position: static !important">
              Incompatible JQuery Version Fix (included in: 1.38.47, 1.71.20 -
              and higher),
              <a
                href="https://github.com/SAP/openui5/blob/master/docs/self_closing_tags_fix_instructions.md"
                target="_blank"
                rel="noopener noreferrer"
                class="sapMLnk"
                style="position: static !important"
                >read more...</a
              >
            </li>
            <li style="position: static !important">
              Reverse Tabnabbing Fix (included in: 1.38.49, 1.71.26, 1.84.4 -
              and higher)
            </li>
          </ul>
        </div>
      </div>
      <button
        id="__button1"
        data-sap-ui="__button1"
        data-sap-ui-render=""
        data-ui5-accesskey=""
        aria-labelledby="__text4"
        aria-describedby="__button1-tooltip"
        title="Schließen"
        class="sapMBtnBase sapMBtn sapMMsgStripCloseButton sapUiSizeCompact"
      >
        <span
          id="__button1-inner"
          class="sapMBtnInner sapMBtnHoverable sapMFocusable sapMBtnIconFirst sapMBtnTransparent"
          ><span
            id="__button1-img"
            data-sap-ui="__button1-img"
            data-sap-ui-render=""
            role="presentation"
            aria-hidden="true"
            data-sap-ui-icon-content=""
            class="sapUiIcon sapUiIconMirrorInRTL sapMBtnCustomIcon sapMBtnIcon sapMBtnIconLeft"
            style="font-family: 'SAP-icons'"
          ></span></span
        ><span id="__button1-tooltip" class="sapUiInvisibleText"
          >Schließen</span
        >
      </button>
    </div>
  </div>
  <h1 class="title">OpenUI5 Versions Maintenance Status</h1>
  <p>
    All available OpenUI5 downloads can be found at
    <a
      class="sapThemeHighlight-asColor"
      href="https://openui5.org/releases/"
      target="_blank"
      rel="noopener noreferrer"
      >https://openui5.org/releases/</a
    >.
  </p>
  <div id="branches" data-sap-ui-area="branches">
    <div
      id="__table0"
      data-sap-ui="__table0"
      data-sap-ui-render=""
      data-sap-ui-fastnavgroup="true"
      data-sap-ui-pasteregion="true"
      class="sapMList sapMListBGTranslucent sapMListTblCnt"
      style="width: 100%"
    >
      <div
        id="__toolbar0"
        data-sap-ui="__toolbar0"
        data-sap-ui-render=""
        data-sap-ui-fastnavgroup="true"
        class="sapMIBar sapMTBInactive sapMTB sapMTBNewFlex sapMTBStandard sapMTB-Transparent-CTX sapMOTB sapMListHdr sapMListHdrTBar sapMTBHeader-CTX"
      >
        <h2
          id="__title0"
          data-sap-ui="__title0"
          data-sap-ui-render=""
          class="sapMTitle sapMTitleStyleAuto sapMTitleNoWrap sapUiSelectable sapMTitleMaxWidth sapMBarChild sapMBarChildFirstChild"
        >
          <span id="__title0-inner" dir="auto"
            >Maintenance Status Overview</span
          >
        </h2>
        <div
          id="__spacer0"
          data-sap-ui="__spacer0"
          data-sap-ui-render=""
          class="sapMTBSpacer sapMTBSpacerFlex sapMBarChild"
        ></div>
        <button
          id="__button2"
          data-sap-ui="__button2"
          data-sap-ui-render=""
          data-ui5-accesskey=""
          aria-label="Toggle Maintenance/All Versions"
          aria-pressed="true"
          title="Toggle Maintenance/All Versions"
          class="sapMBtnBase sapMBtn sapMBarChild"
          @click.stop="mVersionToggle"
        >
          <span
            id="__button2-inner"
            class="sapMBtnInner sapMBtnHoverable sapMFocusable sapMBtnIconFirst sapMToggleBtnPressed sapMBtnDefault"
            ><span
              id="__button2-img"
              data-sap-ui="__button2-img"
              data-sap-ui-render=""
              role="presentation"
              aria-hidden="true"
              data-sap-ui-icon-content=""
              class="sapUiIcon sapUiIconMirrorInRTL sapMBtnCustomIcon sapMBtnIcon sapMBtnIconLeft"
              style="font-family: 'SAP-icons'"
            ></span></span
          ><span id="__button2-tooltip" class="sapUiInvisibleText"
            >Toggle Maintenance/All Versions</span
          ></button
        ><button
          id="__toolbar0-overflowButtonClone"
          data-sap-ui="__toolbar0-overflowButtonClone"
          data-sap-ui-render=""
          data-ui5-accesskey=""
          aria-haspopup="menu"
          aria-pressed="false"
          class="sapMBtnBase sapMBtn sapMTBHiddenElement sapMBarChild"
        >
          <span
            id="__toolbar0-overflowButtonClone-inner"
            class="sapMBtnInner sapMBtnHoverable sapMFocusable sapMBtnIconFirst sapMBtnTransparent"
            ><span
              id="__toolbar0-overflowButtonClone-img"
              data-sap-ui="__toolbar0-overflowButtonClone-img"
              data-sap-ui-render=""
              role="presentation"
              aria-hidden="true"
              data-sap-ui-icon-content=""
              class="sapUiIcon sapUiIconMirrorInRTL sapMBtnCustomIcon sapMBtnIcon sapMBtnIconLeft"
              style="font-family: 'SAP-icons'"
            ></span
          ></span>
        </button>
      </div>
      <div
        id="__table0-before"
        role="none"
        tabindex="-1"
        class="sapMListDummyArea"
      ></div>
      <table
        id="__table0-listUl"
        role="grid"
        aria-labelledby="__title0"
        aria-roledescription="Responsive Tabelle"
        tabindex="0"
        class="sapMListTbl sapMListUl sapMListShowSeparatorsAll sapMListModeNone"
        aria-colcount="5"
        aria-rowcount="9"
      >
        <thead class="sapMTableTHead">
          <tr
            id="__table0-tblHeader"
            role="row"
            tabindex="-1"
            aria-rowindex="1"
            class="sapMListTblRow sapMListTblHeader sapMLIBFocusable sapMTableRowCustomFocus"
          >
            <th
              id="__table0-tblHeadHighlight"
              role="presentation"
              class="sapMTableTH sapMListTblHighlightCol"
            ></th>
            <th
              id="__column0"
              data-sap-ui="__column0"
              aria-colindex="1"
              tabindex="-1"
              role="columnheader"
              data-sap-ui-column="__column0"
              class="sapMListTblCell sapMTblCellFocusable sapMTableTH sapMListTblHeaderCell"
            >
              <div
                id="__column0-ah"
                class="sapMColumnHeader"
                style="justify-content: flex-start; text-align: left"
              >
                <span
                  id="__label0"
                  data-sap-ui="__label0"
                  data-sap-ui-render=""
                  class="sapMLabel sapUiSelectable sapMLabelMaxWidth sapMColumnHeaderContent"
                  style="font-weight: bold; text-align: left"
                  ><span id="__label0-text" class="sapMLabelTextWrapper"
                    ><bdi id="__label0-bdi">Version</bdi></span
                  ><span
                    data-colon=":"
                    aria-hidden="true"
                    class="sapMLabelColonAndRequired"
                  ></span
                ></span>
              </div>
            </th>
            <th
              id="__column1"
              data-sap-ui="__column1"
              aria-colindex="2"
              tabindex="-1"
              role="columnheader"
              data-sap-ui-column="__column1"
              class="sapMListTblCell sapMTblCellFocusable sapMTableTH sapMListTblHeaderCell"
            >
              <div
                id="__column1-ah"
                class="sapMColumnHeader"
                style="justify-content: flex-start; text-align: left"
              >
                <span
                  id="__label1"
                  data-sap-ui="__label1"
                  data-sap-ui-render=""
                  class="sapMLabel sapUiSelectable sapMLabelMaxWidth sapMColumnHeaderContent"
                  style="font-weight: bold; text-align: left"
                  ><span id="__label1-text" class="sapMLabelTextWrapper"
                    ><bdi id="__label1-bdi">Latest Patch</bdi></span
                  ><span
                    data-colon=":"
                    aria-hidden="true"
                    class="sapMLabelColonAndRequired"
                  ></span
                ></span>
              </div>
            </th>
            <th
              id="__column2"
              data-sap-ui="__column2"
              aria-colindex="3"
              tabindex="-1"
              role="columnheader"
              data-sap-ui-column="__column2"
              class="sapMListTblCell sapMTblCellFocusable sapMTableTH sapMListTblHeaderCell"
            >
              <div
                id="__column2-ah"
                class="sapMColumnHeader"
                style="justify-content: flex-start; text-align: left"
              >
                <span
                  id="__label2"
                  data-sap-ui="__label2"
                  data-sap-ui-render=""
                  class="sapMLabel sapUiSelectable sapMLabelMaxWidth sapMColumnHeaderContent"
                  style="font-weight: bold; text-align: left"
                  ><span id="__label2-text" class="sapMLabelTextWrapper"
                    ><bdi id="__label2-bdi">Maintenance Status</bdi></span
                  ><span
                    data-colon=":"
                    aria-hidden="true"
                    class="sapMLabelColonAndRequired"
                  ></span
                ></span>
              </div>
            </th>
            <th
              id="__column3"
              data-sap-ui="__column3"
              aria-colindex="4"
              tabindex="-1"
              role="columnheader"
              data-sap-ui-column="__column3"
              class="sapMListTblCell sapMTblCellFocusable sapMTableTH sapMListTblHeaderCell"
            >
              <div
                id="__column3-ah"
                class="sapMColumnHeader"
                style="justify-content: flex-start; text-align: left"
              >
                <span
                  id="__label3"
                  data-sap-ui="__label3"
                  data-sap-ui-render=""
                  class="sapMLabel sapUiSelectable sapMLabelMaxWidth sapMColumnHeaderContent"
                  style="font-weight: bold; text-align: left"
                  ><span id="__label3-text" class="sapMLabelTextWrapper"
                    ><bdi id="__label3-bdi">End of Maintenance</bdi></span
                  ><span
                    data-colon=":"
                    aria-hidden="true"
                    class="sapMLabelColonAndRequired"
                  ></span
                ></span>
              </div>
            </th>
            <th
              id="__column4"
              data-sap-ui="__column4"
              aria-colindex="5"
              tabindex="-1"
              role="columnheader"
              data-sap-ui-column="__column4"
              class="sapMListTblCell sapMTblCellFocusable sapMTableTH sapMListTblHeaderCell"
            >
              <div
                id="__column4-ah"
                class="sapMColumnHeader"
                style="justify-content: flex-start; text-align: left"
              >
                <span
                  id="__label4"
                  data-sap-ui="__label4"
                  data-sap-ui-render=""
                  class="sapMLabel sapUiSelectable sapMLabelMaxWidth sapMColumnHeaderContent"
                  style="font-weight: bold; text-align: left"
                  ><span id="__label4-text" class="sapMLabelTextWrapper"
                    ><bdi id="__label4-bdi"
                      >End of Cloud Provisioning</bdi
                    ></span
                  ><span
                    data-colon=":"
                    aria-hidden="true"
                    class="sapMLabelColonAndRequired"
                  ></span
                ></span>
              </div>
            </th>
            <th
              id="__table0-tblHeadNavigated"
              role="presentation"
              class="sapMTableTH sapMListTblNavigatedCol"
            ></th>
          </tr>
        </thead>
        <tbody id="__table0-tblBody" class="sapMListItems sapMTableTBody">
          <tr
            v-for="(row, index) in mVersionCp"
            :key="index"
            data-sap-ui="__item0-__table0-0"
            data-sap-ui-render=""
            tabindex="-1"
            role="row"
            aria-rowindex="2"
            class="sapMLIB sapMLIB-CTX sapMLIBShowSeparator sapMLIBTypeActive sapMLIBActionable sapMLIBHoverable sapMLIBFocusable sapMListTblRow"
            @click.stop="aVersionSearch = row.version"
          >
            <td role="presentation" class="sapMListTblHighlightCell"></td>
            <td
              role="gridcell"
              aria-colindex="1"
              tabindex="-1"
              data-sap-ui-column="__column0"
              class="sapMListTblCell sapMTblCellFocusable"
              style="text-align: left"
            >
              <div
                data-sap-ui="__text7-__table0-0"
                data-sap-ui-render=""
                class="sapMFT"
                style=""
              >
                <strong style="position: static !important">{{
                  row.version
                }}</strong>
              </div>
            </td>
            <td
              role="gridcell"
              aria-colindex="2"
              tabindex="-1"
              data-sap-ui-column="__column1"
              class="sapMListTblCell sapMTblCellFocusable"
              style="text-align: left"
            >
              <span
                data-sap-ui="__text8-__table0-0"
                data-sap-ui-render=""
                dir="auto"
                class="sapMText sapUiSelectable sapMTextBreakWord sapMTextMaxWidth"
                style="text-align: left"
                >{{ row.latest }}</span
              >
            </td>
            <td
              role="gridcell"
              aria-colindex="3"
              tabindex="-1"
              data-sap-ui-column="__column2"
              class="sapMListTblCell sapMTblCellFocusable"
              style="text-align: left"
            >
              <span
                data-sap-ui="__text9-__table0-0"
                data-sap-ui-render=""
                dir="auto"
                class="sapMText sapUiSelectable sapMTextBreakWord sapMTextMaxWidth maintenance"
                style="text-align: left"
                >{{ row.maintaine }}</span
              >
            </td>
            <td
              role="gridcell"
              aria-colindex="4"
              tabindex="-1"
              data-sap-ui-column="__column3"
              class="sapMListTblCell sapMTblCellFocusable"
              style="text-align: left"
            >
              <span
                data-sap-ui="__text10-__table0-0"
                data-sap-ui-render=""
                dir="auto"
                class="sapMText sapUiSelectable sapMTextBreakWord sapMTextMaxWidth"
                style="text-align: left"
                >{{ row.eom }}</span
              >
            </td>
            <td
              role="gridcell"
              aria-colindex="5"
              tabindex="-1"
              data-sap-ui-column="__column4"
              class="sapMListTblCell sapMTblCellFocusable"
              style="text-align: left"
            >
              <span
                data-sap-ui="__text11-__table0-0"
                data-sap-ui-render=""
                dir="auto"
                class="sapMText sapUiSelectable sapMTextBreakWord sapMTextMaxWidth"
                style="text-align: left"
                >{{ row.eocp }}</span
              >
            </td>
            <td role="presentation" class="sapMListTblNavigatedCell"></td>
          </tr>
        </tbody>
      </table>
      <div
        id="__table0-after"
        role="none"
        tabindex="0"
        class="sapMListDummyArea sapMListDummyAreaSticky"
      ></div>
    </div>
  </div>
  <h1 class="title">Available OpenUI5 Versions</h1>
  <div
    id="versionsMessages"
    class="messages"
    data-sap-ui-area="versionsMessages"
  >
    <div
      id="__strip2"
      data-sap-ui="__strip2"
      data-sap-ui-render=""
      data-sap-ui-fastnavgroup="true"
      data-sap-ui-ms-closable="true"
      role="note"
      aria-labelledby="__strip2"
      aria-roledescription="Informationsleiste"
      class="sapMMsgStrip sapMMsgStripInformation"
    >
      <span id="__strip2-info" class="sapUiPseudoInvisibleText"
        >Nachrichtenzeile für Informationen Schließbar</span
      >
      <div class="sapMMsgStripIcon">
        <span
          data-sap-ui-icon-content=""
          role="presentation"
          aria-hidden="true"
          id="id-1699627596560-13"
          aria-label="information"
          class="sapUiIcon sapUiIconMirrorInRTL"
          style="font-family: 'SAP-icons'"
        ></span>
      </div>
      <div id="__strip2-content" class="sapMMsgStripMessage">
        <span
          id="__text14"
          data-sap-ui="__text14"
          data-sap-ui-render=""
          dir="auto"
          class="sapMText sapUiSelectable sapMTextMaxWidth"
          style="text-align: left"
          >"To Be Determined" as value of "End of Cloud Provisioning" is set to
          the latest released versions. It will be updated with concrete year
          quarter value after the next version is released. Calculated a year
          after the point in time of "next" version release.</span
        >
      </div>
      <button
        id="__button3"
        data-sap-ui="__button3"
        data-sap-ui-render=""
        data-ui5-accesskey=""
        aria-labelledby="__text15"
        aria-describedby="__button3-tooltip"
        title="Schließen"
        class="sapMBtnBase sapMBtn sapMMsgStripCloseButton sapUiSizeCompact"
      >
        <span
          id="__button3-inner"
          class="sapMBtnInner sapMBtnHoverable sapMFocusable sapMBtnIconFirst sapMBtnTransparent"
          ><span
            id="__button3-img"
            data-sap-ui="__button3-img"
            data-sap-ui-render=""
            role="presentation"
            aria-hidden="true"
            data-sap-ui-icon-content=""
            class="sapUiIcon sapUiIconMirrorInRTL sapMBtnCustomIcon sapMBtnIcon sapMBtnIconLeft"
            style="font-family: 'SAP-icons'"
          ></span></span
        ><span id="__button3-tooltip" class="sapUiInvisibleText"
          >Schließen</span
        >
      </button>
    </div>
  </div>
  <div id="versions" data-sap-ui-area="versions">
    <div
      id="__table1"
      data-sap-ui="__table1"
      data-sap-ui-render=""
      data-sap-ui-fastnavgroup="true"
      data-sap-ui-pasteregion="true"
      class="sapMList sapMListBGTranslucent sapMListTblCnt"
      style="width: 100%"
    >
      <div
        id="__toolbar1"
        data-sap-ui="__toolbar1"
        data-sap-ui-render=""
        data-sap-ui-fastnavgroup="true"
        class="sapMIBar sapMTBInactive sapMTB sapMTBNewFlex sapMTBStandard sapMTB-Transparent-CTX sapMOTB sapMListHdr sapMListHdrTBar sapMTBHeader-CTX"
      >
        <h2
          id="__title1"
          data-sap-ui="__title1"
          data-sap-ui-render=""
          class="sapMTitle sapMTitleStyleAuto sapMTitleNoWrap sapUiSelectable sapMTitleMaxWidth sapMBarChild sapMBarChildFirstChild"
        >
          <span id="__title1-inner" dir="auto">Patch Version Overview</span>
        </h2>
        <div
          id="__spacer1"
          data-sap-ui="__spacer1"
          data-sap-ui-render=""
          class="sapMTBSpacer sapMTBSpacerFlex sapMBarChild"
        ></div>
        <div
          id="__field0"
          data-sap-ui="__field0"
          data-sap-ui-render=""
          class="sapMSF sapMBarChild"
          style="width: 15em"
        >
          <form id="__field0-F" class="sapMSFF">
            <span
              id="__field0-staticSearchIcon"
              aria-hidden="true"
              class="sapMSFSSI"
            ></span
            ><input
              id="__field0-I"
              type="search"
              aria-label="Suchen"
              autocomplete="off"
              placeholder="Suchen"
              v-model="aVersionSearch"
              aria-describedby="__text18"
              class="sapMSFI"
            />
            <div
              id="__field0-reset"
              aria-hidden="true"
              class="sapMSFR sapMSFB sapMSFBF"
            ></div>
            <div
              id="__field0-search"
              aria-hidden="true"
              class="sapMSFS sapMSFB sapMSFBF"
            ></div>
          </form>
        </div>
        <button
          id="__toolbar1-overflowButtonClone"
          data-sap-ui="__toolbar1-overflowButtonClone"
          data-sap-ui-render=""
          data-ui5-accesskey=""
          aria-haspopup="menu"
          aria-pressed="false"
          class="sapMBtnBase sapMBtn sapMTBHiddenElement sapMBarChild"
        >
          <span
            id="__toolbar1-overflowButtonClone-inner"
            class="sapMBtnInner sapMBtnHoverable sapMFocusable sapMBtnIconFirst sapMBtnTransparent"
            ><span
              id="__toolbar1-overflowButtonClone-img"
              data-sap-ui="__toolbar1-overflowButtonClone-img"
              data-sap-ui-render=""
              role="presentation"
              aria-hidden="true"
              data-sap-ui-icon-content=""
              class="sapUiIcon sapUiIconMirrorInRTL sapMBtnCustomIcon sapMBtnIcon sapMBtnIconLeft"
              style="font-family: 'SAP-icons'"
            ></span
          ></span>
        </button>
      </div>
      <div
        id="__table1-before"
        role="none"
        tabindex="-1"
        class="sapMListDummyArea"
      ></div>
      <table
        id="__table1-listUl"
        role="grid"
        aria-labelledby="__title1"
        aria-roledescription="Responsive Tabelle"
        tabindex="0"
        class="sapMListTbl sapMListUl sapMListShowSeparatorsAll sapMListModeNone"
        aria-colcount="3"
        aria-rowcount="113"
      >
        <thead class="sapMTableTHead">
          <tr
            id="__table1-tblHeader"
            role="row"
            tabindex="-1"
            aria-rowindex="1"
            class="sapMListTblRow sapMListTblHeader sapMLIBFocusable sapMTableRowCustomFocus"
          >
            <th
              id="__table1-tblHeadHighlight"
              role="presentation"
              class="sapMTableTH sapMListTblHighlightCol"
            ></th>
            <th
              id="__column5"
              data-sap-ui="__column5"
              aria-colindex="1"
              tabindex="-1"
              role="columnheader"
              data-sap-ui-column="__column5"
              class="sapMListTblCell sapMTblCellFocusable sapMTableTH sapMListTblHeaderCell"
            >
              <div
                id="__column5-ah"
                class="sapMColumnHeader"
                style="justify-content: flex-start; text-align: left"
              >
                <span
                  id="__label5"
                  data-sap-ui="__label5"
                  data-sap-ui-render=""
                  class="sapMLabel sapUiSelectable sapMLabelMaxWidth sapMColumnHeaderContent"
                  style="font-weight: bold; text-align: left"
                  ><span id="__label5-text" class="sapMLabelTextWrapper"
                    ><bdi id="__label5-bdi">Version</bdi></span
                  ><span
                    data-colon=":"
                    aria-hidden="true"
                    class="sapMLabelColonAndRequired"
                  ></span
                ></span>
              </div>
            </th>
            <th
              id="__column6"
              data-sap-ui="__column6"
              aria-colindex="2"
              tabindex="-1"
              role="columnheader"
              data-sap-ui-column="__column6"
              class="sapMListTblCell sapMTblCellFocusable sapMTableTH sapMListTblHeaderCell"
            >
              <div
                id="__column6-ah"
                class="sapMColumnHeader"
                style="justify-content: flex-start; text-align: left"
              >
                <span
                  id="__label6"
                  data-sap-ui="__label6"
                  data-sap-ui-render=""
                  class="sapMLabel sapUiSelectable sapMLabelMaxWidth sapMColumnHeaderContent"
                  style="font-weight: bold; text-align: left"
                  ><span id="__label6-text" class="sapMLabelTextWrapper"
                    ><bdi id="__label6-bdi">Patches</bdi></span
                  ><span
                    data-colon=":"
                    aria-hidden="true"
                    class="sapMLabelColonAndRequired"
                  ></span
                ></span>
              </div>
            </th>
            <th
              id="__column7"
              data-sap-ui="__column7"
              aria-colindex="3"
              tabindex="-1"
              role="columnheader"
              data-sap-ui-column="__column7"
              class="sapMListTblCell sapMTblCellFocusable sapMTableTH sapMListTblHeaderCell"
            >
              <div
                id="__column7-ah"
                class="sapMColumnHeader"
                style="justify-content: flex-start; text-align: left"
              >
                <span
                  id="__label7"
                  data-sap-ui="__label7"
                  data-sap-ui-render=""
                  class="sapMLabel sapUiSelectable sapMLabelMaxWidth sapMColumnHeaderContent"
                  style="font-weight: bold; text-align: left"
                  ><span id="__label7-text" class="sapMLabelTextWrapper"
                    ><bdi id="__label7-bdi"
                      >End of Cloud Provisioning</bdi
                    ></span
                  ><span
                    data-colon=":"
                    aria-hidden="true"
                    class="sapMLabelColonAndRequired"
                  ></span
                ></span>
              </div>
            </th>
            <th
              id="__table1-tblHeadNavigated"
              role="presentation"
              class="sapMTableTH sapMListTblNavigatedCol"
            ></th>
          </tr>
        </thead>
        <tbody id="__table1-tblBody" class="sapMListItems sapMTableTBody">
          <tr
            v-for="(row, index) in aVersionCP"
            :key="index"
            data-sap-ui="__item1-__table1-0"
            data-sap-ui-render=""
            tabindex="-1"
            role="row"
            aria-rowindex="2"
            class="sapMLIB sapMLIB-CTX sapMLIBShowSeparator sapMLIBTypeInactive sapMLIBFocusable sapMListTblRow"
          >
            <td role="presentation" class="sapMListTblHighlightCell"></td>
            <td
              role="gridcell"
              aria-colindex="1"
              tabindex="-1"
              data-sap-ui-column="__column5"
              class="sapMListTblCell sapMTblCellFocusable"
              style="text-align: left"
            >
              <span
                data-sap-ui="__text16-__table1-0"
                data-sap-ui-render=""
                dir="auto"
                class="sapMText sapUiSelectable sapMTextBreakWord sapMTextMaxWidth"
                style="text-align: left"
                >{{ row.version }}</span
              >
            </td>
            <td
              role="gridcell"
              aria-colindex="2"
              tabindex="-1"
              data-sap-ui-column="__column6"
              class="sapMListTblCell sapMTblCellFocusable"
              style="text-align: left"
            >
              <a
                data-sap-ui="__link0-__table1-0"
                data-sap-ui-render=""
                href="/1.120.1/versioninfo.html"
                tabindex="0"
                target="_blank"
                rel="noopener noreferrer"
                class="sapMLnk sapMLnkMaxWidth"
                >{{ row.patches }}</a
              >
            </td>
            <td
              role="gridcell"
              aria-colindex="3"
              tabindex="-1"
              data-sap-ui-column="__column7"
              class="sapMListTblCell sapMTblCellFocusable"
              style="text-align: left"
            >
              <span
                data-sap-ui="__text17-__table1-0"
                data-sap-ui-render=""
                dir="auto"
                class="sapMText sapUiSelectable sapMTextMaxWidth"
                style="text-align: left"
                >{{ row.eod }}</span
              >
            </td>
            <td role="presentation" class="sapMListTblNavigatedCell"></td>
          </tr>
        </tbody>
      </table>
      <div
        id="__table1-after"
        role="none"
        tabindex="0"
        class="sapMListDummyArea sapMListDummyAreaSticky"
      ></div>
    </div>
  </div>
  <footer>
    <!-- <img
      src="./resources/sap/ui/documentation/sdk/images/logo_sap.png"
      style="width: 3rem; height: 1.5rem"
    /> -->
    <a
      class="sapMLnk"
      href="https://www.sap.com/corporate/en/legal/impressum.html"
      target="_blank"
      rel="noopener noreferrer"
      >Legal Disclosure</a
    >
    <span class="sapMLnk"> | </span>
    <a
      class="sapMLnk"
      href="https://www.sap.com/corporate/en/legal/privacy.html"
      target="_blank"
      rel="noopener noreferrer"
      >Privacy</a
    >
    <span class="sapMLnk"> | </span>
    <a
      class="sapMLnk"
      href="https://www.sap.com/corporate/en/legal/terms-of-use.html"
      target="_blank"
      rel="noopener noreferrer"
      >Terms of Use</a
    >
  </footer>

  <div
    aria-hidden="true"
    id="sap-ui-preserve"
    class="sapUiHidden sapUiForcedHidden"
    style="width: 0px; height: 0px; overflow: hidden"
  ></div>
</template>

<style scoped></style>
