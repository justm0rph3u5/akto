<template>
    <div class="pa-3 set-config-div">
        <div class="config-heading">Attacker Token</div>
        <div class="spinner-div" v-if="authMechanismLoading">
            <spinner :size="50"/>
        </div>
        <div v-else>
            <div>
                <div style="margin-top: 20px;"></div>
                <div class="form-key">
                    <div>Auth header key</div>
                    <hint-icon value="Attacker token header key"/>
                </div>
                <div style="margin-top: 4px">
                    <v-text-field
                        placeholder=""
                        type="text"
                        required
                        dense
                        outlined
                        class="auth-text-field"
                        background-color="#F9F9FA"
                        v-model="authKey"
                    />
                </div>
            </div>
            <div>
                <div class="form-key">
                    <div>Auth header value</div>
                    <hint-icon value="Attacker token value"/>
                </div>
                <div style="margin-top: 4px">
                    <v-textarea
                        placeholder=""
                        type="text"
                        required
                        dense
                        multi
                        outlined
                        class="auth-text-field"
                        rows="3"
                        background-color="#F9F9FA"
                        v-model="authValue"
                    />
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import {mapState} from 'vuex'
import Spinner from '@/apps/dashboard/shared/components/Spinner'
import HintIcon from "./HintIcon";

export default {
    name: "SetConfig",
    components: {
        Spinner,
        HintIcon
    },
    data () {
        return {
        }
    },
    mounted() {
    },
    computed: {
        ...mapState('onboarding', ['authMechanismLoading']),
        authKey:{
            get() {
                return this.$store.state.onboarding.authKey
            },
            set(v) {
                this.$store.state.onboarding.authKey = v
            }
        },
        authValue:{
            get() {
                return this.$store.state.onboarding.authValue
            },
            set(v) {
                this.$store.state.onboarding.authValue = v
            }
        }
    },
}


</script>

<style lang="sass" style="scoped">

.auth-text-field.v-input .v-input__slot 
    border-radius: 8px

.auth-text-field.v-text-field--outlined fieldset 
    color: var(--hexColor22) !important

.set-config-div
    width: 550px
    height: 250px
    margin-bottom: 36px

.spinner-div
    display: flex
    justify-content: center
    height: 100%
    align-items: center

.form-key
    display: flex
    align-items: center
    font-weight: 400
    font-size: 14px
    color: var(--themeColorDark)

.config-heading
    font-weight: 500
    font-size: 20px
    color: var(--themeColorDark)

</style>