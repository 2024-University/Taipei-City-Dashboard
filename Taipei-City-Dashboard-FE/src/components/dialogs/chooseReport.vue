<!-- eslint-disable indent -->
<!-- eslint-disable no-mixed-spaces-and-tabs -->
<!-- Developed by Taipei Urban Intelligence Center 2023-2024-->

<script setup>
import { computed } from "vue";
import { useDialogStore } from "../../store/dialogStore";

import DialogContainer from "./DialogContainer.vue";
import ReportIssue from "./ReportIssue.vue";
import ReportStopPower from "./ReportStopPower.vue";

const dialogStore = useDialogStore();

function handleClose() {
	dialogStore.dialogs.chooseReport = false;
}

function openrpissue() {
	dialogStore.dialogs.reportIssue = true;
}

function openrpsPower() {
	dialogStore.dialogs.reportStopPower = true;
}
</script>

<template>
  <DialogContainer
    dialog="chooseReport"
    @on-close="handleClose"
  >
    <div class="choosecomponent">
		<div class="choosecomponent-control">
        <button
          class="choosecomponent-control-confirm"
          @click="openrpissue"
        >
          系統問題回報
        </button>
      </div>
      <div class="choosecomponent-control">
        <button
          class="choosecomponent-control-confirm"
          @click="openrpsPower"
        >
          停電回報
        </button>
      </div>
    </div>
	<ReportIssue />
	<ReportStopPower />
  </DialogContainer>
</template>

<style scoped lang="scss">
.choosecomponent {
	width: 300px;

	&-control {
		display: flex;
		justify-content: center;

		&-confirm {
			margin: 15px 2px;
			padding: 4px 10px;
			border-radius: 5px;
			background-color: var(--color-highlight);
			transition: opacity 0.2s;

			&:hover {
				opacity: 0.8;
			}
		}
	}
}
</style>
