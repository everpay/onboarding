<template>
    <div id="app">

        <form-wizard>

            <template v-slot="{formData}">
                <h1>UNCLASSIFIED/FOUO ONLY</h1>

                <tab name="Step 1" info="Header" :selected="true" :formData="formData" num="1">
                    <h2>Header Information</h2>
                    <div id="form-step-1">
                        <div class="field">
                            <label class="label">Copies</label>
                            <div class="control">
                                <input class="input" name="copies" type="text" placeholder="Copy ## of ## copies"
                                       v-model="formData.header1" data-vv-scope="step1" v-validate="'required'">
                                <p class="help is-danger" v-show="errors.has('step1.copies')">
                                    {{ errors.first('step1.copies') }}
                                </p>
                            </div>
                        </div>
                        <div class="field">
                            <label class="label">Issuing headuarters</label>
                            <div class="control">
                                <input class="input" name="headquarters" type="text"
                                       placeholder="example: 1st Infantry Division" v-model="formData.header2"
                                       data-vv-scope="step1" v-validate="'required'">
                                <p class="help is-danger" v-show="errors.has('step1.headquarters')">
                                    {{ errors.first('step1.headquarters') }}
                                </p>
                            </div>
                        </div>
                        <div class="field">
                            <label class="label">Place of Issue</label>
                            <div class="control">
                                <input class="input" name="place of issue" type="text"
                                       placeholder="code name, postal designation, or geographic location."
                                       v-model="formData.header3" data-vv-scope="step1" v-validate="'required'">
                                <p class="help is-danger" v-show="errors.has('step1.place of issue')">
                                    {{ errors.first('step1.place of issue') }}
                                </p>
                            </div>
                        </div>
                        <div class="field">
                            <label class="label">Date-time group of signature</label>
                            <div class="control">
                                <input class="input" name="date time group" type="text" placeholder="DDHHMM(Z)MONYY"
                                       v-model="formData.header4" data-vv-scope="step1" v-validate="'required'">
                                <p class="help is-danger" v-show="errors.has('step1.date time group')">
                                    {{ errors.first('step1.date time group') }}
                                </p>
                            </div>
                        </div>
                        <div class="field">
                            <label class="label">Message reference number</label>
                            <div class="control">
                                <input class="input" name="message reference number" type="text"
                                       placeholder="List maps and charts first, followed by other references"
                                       v-model="formData.header5" data-vv-scope="step1">
                                <p class="help is-danger" v-show="errors.has('step1.message reference number')">
                                    {{ errors.first('step1.message reference number') }}
                                </p>
                            </div>
                        </div>
                        <div class="field">
                            <label class="label">Reference</label>
                            <div class="control">
                                <input class="input" name="reference" type="text"
                                       placeholder="List maps and charts first, followed by other references"
                                       v-model="formData.references1" data-vv-scope="step1">

                            </div>
                        </div>
                        <div class="field">
                            <label class="label">Reference</label>
                            <div class="control">
                                <input class="input" name="reference" type="text"
                                       placeholder="List maps and charts first, followed by other references"
                                       v-model="formData.references2" data-vv-scope="step1">

                            </div>
                        </div>
                        <div class="field">
                            <label class="label">Reference</label>
                            <div class="control">
                                <input class="input" name="reference" type="text"
                                       placeholder="List maps and charts first, followed by other references"
                                       v-model="formData.references3" data-vv-scope="step1">

                            </div>
                        </div>
                        <div class="field">
                            <label class="label">Reference</label>
                            <div class="control">
                                <input class="input" name="reference" type="text"
                                       placeholder="headquarters internal control number assigned to all plans and orders"
                                       v-model="formData.references4" data-vv-scope="step1">
                            </div>
                        </div>
                        <div class="field">
                            <label class="label">Time Zone Used Throughout the OPORD</label>
                            <div class="control">
                                <input class="input" name="time zone" type="text"
                                       placeholder="time zone used in the area of operations during execution."
                                       v-model="formData.timeZone" data-vv-scope="step1">
                            </div>
                        </div>
                        <div class="field">
                            <label class="label">Task Organization</label>
                            <div class="control">
                          <textarea class="textarea" name="task organization" type="text"
                                    placeholder="Describe the organization of forces available to the issuing headquarters and their command and support relationships. Refer to Annex A (Task Organization) if long or complicated."
                                    v-model="formData.taskOrg" data-vv-scope="step1" ></textarea>
                            </div>
                        </div>
                    </div>
                </tab>

                <tab name="Step 2" info="Situation" data-vv-scope="step2" num="2">
                    <div id="form-step-2">
                        <div class="field">
                          <label class="label">Area of Interest</label>
                            <div class="control">
                                <textarea class="textarea" name="area of interest" v-model="formData.situation1"
                                          placeholder="Describe the area of interest. Refer to Annex B (Intelligence) as required."
                                          v-validate="'required'" data-vv-scope="step2"></textarea>
                                <p class="help is-danger" v-show="errors.has('step2.area of interest')">
                                    {{ errors.first('step2.area of interest') }}
                                </p>
                            </div>
                        </div>
                        <div class="field">
                            <label class="label">Area of Operations</label>
                            <div class="control">
                                <textarea class="textarea" name="area of operations" v-model="formData.situation2"
                                          placeholder="Describe the area of operations. Refer to the appropriate map by its subparagraph under references, for example, “Map, reference (b).” See Appendix 2 (Operation Overlay) to Annex C (Operations) as required."
                                          v-validate="'required'" data-vv-scope="step2"></textarea>
                                <p class="help is-danger" v-show="errors.has('step2.area of operations')">
                                    {{ errors.first('step2.area of operations') }}
                                </p>
                            </div>
                        </div>
                        <div class="field">
                            <label class="label">Terrain</label>
                            <div class="control">
                                <textarea class="input" name="terrain" v-model="formData.situation3"
                                          placeholder="Describe the aspects of terrain that impact operations. Refer to Annex B (Intelligence) as required."
                                          v-validate="'required'" data-vv-scope="step2"></textarea>
                                <p class="help is-danger" v-show="errors.has('step2.terrain')">
                                    {{ errors.first('step2.terrain') }}
                                </p>
                            </div>
                        </div>
                        <div class="field">
                            <label class="label">Weather</label>
                            <div class="control">
                                <textarea class="input" name="weather" v-model="formData.situation4"
                                          placeholder="Describe the aspects of weather that impact operations. Refer to Annex B (Intelligence) as required."
                                          v-validate="'required'" data-vv-scope="step2"></textarea>
                                <p class="help is-danger" v-show="errors.has('step2.weather')">
                                    {{ errors.first('step2.weather') }}
                                </p>
                            </div>
                        </div>
                        <div class="field">
                            <label class="label">Enemy Forces</label>
                            <div class="control">
                                <textarea class="textarea" name="enemy forces" v-model="formData.situation5"
                                          placeholder="Describe the enemy forces. Refer to Annex B (Intelligence) as required."
                                          v-validate="'required'" data-vv-scope="step2"></textarea>
                                <p class="help is-danger" v-show="errors.has('step2.enemy forces')">
                                    {{ errors.first('step2.enemy forces') }}
                                </p>
                            </div>
                        </div>

                    </div>
                </tab>
                
                <tab name="Step 3" info="Mission" num="3">
                    <div id="form-step-3">
                        <div class="field">
                            <label class="label">step 3?</label>
                            <div class="control">
                                <div class="select" name="reference">
                                    <select v-model="formData.reference" v-validate="'required'" name="reference"
                                            data-vv-scope="step3">
                                        <option value="">Select</option>
                                        <option value="newspaper">Newspaper</option>
                                        <option value="social-media">Social Media</option>
                                        <option value="other">Other</option>
                                    </select>
                                </div>
                            </div>
                            <p class="help is-danger" v-show="errors.has('step3.reference')">
                                {{ errors.first('step3.reference') }}
                            </p>
                        </div>
                        <div class="field">
                            <div class="control">
                                <label class="checkbox">
                                    <input type="checkbox" name="terms" v-model="formData.terms" data-vv-scope="step3"
                                           v-validate="'required'">
                                    I agree to the <a href="#">terms and conditions</a>
                                </label>
                            </div>
                            <p class="help is-danger" v-show="errors.has('step3.terms')">
                                {{ errors.first('step3.terms') }}
                            </p>
                        </div>
                    </div>
                </tab>
                <tab name="Step 4" info="Execution" num="4">
                    <div id="form-step-4">
                        <div class="field">
                            <label class="label">Where did you hear about us?</label>
                            <div class="control">
                                <div class="select" name="reference">
                                    <select v-model="formData.reference" v-validate="'required'" name="reference"
                                            data-vv-scope="step3">
                                        <option value="">Select</option>
                                        <option value="newspaper">Newspaper</option>
                                        <option value="social-media">Social Media</option>
                                        <option value="other">Other</option>
                                    </select>
                                </div>
                            </div>
                            <p class="help is-danger" v-show="errors.has('step3.reference')">
                                {{ errors.first('step3.reference') }}
                            </p>
                        </div>
                        <div class="field">
                            <div class="control">
                                <label class="checkbox">
                                    <input type="checkbox" name="terms" v-model="formData.terms" data-vv-scope="step3"
                                           v-validate="'required'">
                                    I agree to the <a href="#">terms and conditions</a>
                                </label>
                            </div>
                            <p class="help is-danger" v-show="errors.has('step3.terms')">
                                {{ errors.first('step3.terms') }}
                            </p>
                        </div>
                    </div>
                </tab>
                <tab name="Step 5" info="Sustainment" num="5">
                    <div id="form-step-5">
                        <div class="field">
                            <label class="label">Where did you hear about us?</label>
                            <div class="control">
                                <div class="select" name="reference">
                                    <select v-model="formData.reference" v-validate="'required'" name="reference"
                                            data-vv-scope="step3">
                                        <option value="">Select</option>
                                        <option value="newspaper">Newspaper</option>
                                        <option value="social-media">Social Media</option>
                                        <option value="other">Other</option>
                                    </select>
                                </div>
                            </div>
                            <p class="help is-danger" v-show="errors.has('step3.reference')">
                                {{ errors.first('step3.reference') }}
                            </p>
                        </div>
                        <div class="field">
                            <div class="control">
                                <label class="checkbox">
                                    <input type="checkbox" name="terms" v-model="formData.terms" data-vv-scope="step3"
                                           v-validate="'required'">
                                    I agree to the <a href="#">terms and conditions</a>
                                </label>
                            </div>
                            <p class="help is-danger" v-show="errors.has('step3.terms')">
                                {{ errors.first('step3.terms') }}
                            </p>
                        </div>
                    </div>
                </tab>
                <tab name="Step 6" info="Command & Signal" num="6">
                    <div id="form-step-6">
                        <div class="field">
                            <label class="label">Where did you hear about us?</label>
                            <div class="control">
                                <div class="select" name="reference">
                                    <select v-model="formData.reference" v-validate="'required'" name="reference"
                                            data-vv-scope="step3">
                                        <option value="">Select</option>
                                        <option value="newspaper">Newspaper</option>
                                        <option value="social-media">Social Media</option>
                                        <option value="other">Other</option>
                                    </select>
                                </div>
                            </div>
                            <p class="help is-danger" v-show="errors.has('step3.reference')">
                                {{ errors.first('step3.reference') }}
                            </p>
                        </div>
                        <div class="field">
                            <div class="control">
                                <label class="checkbox">
                                    <input type="checkbox" name="terms" v-model="formData.terms" data-vv-scope="step3"
                                           v-validate="'required'">
                                    I agree to the <a href="#">terms and conditions</a>
                                </label>
                            </div>
                            <p class="help is-danger" v-show="errors.has('step3.terms')">
                                {{ errors.first('step3.terms') }}
                            </p>
                        </div>
                    </div>
                </tab>
                <tab name="Step 7" info="Confirmation" num="7">
                    <div id="form-step-7">
                        <div class="field">
                            <label class="label">Where did you hear about us?</label>
                            <div class="control">
                                <div class="select" name="reference">
                                    <select v-model="formData.reference" v-validate="'required'" name="reference"
                                            data-vv-scope="step3">
                                        <option value="">Select</option>
                                        <option value="newspaper">Newspaper</option>
                                        <option value="social-media">Social Media</option>
                                        <option value="other">Other</option>
                                    </select>
                                </div>
                            </div>
                            <p class="help is-danger" v-show="errors.has('step3.reference')">
                                {{ errors.first('step3.reference') }}
                            </p>
                        </div>
                        <div class="field">
                            <div class="control">
                                <label class="checkbox">
                                    <input type="checkbox" name="terms" v-model="formData.terms" data-vv-scope="step3"
                                           v-validate="'required'">
                                    I agree to the <a href="#">terms and conditions</a>
                                </label>
                            </div>
                            <p class="help is-danger" v-show="errors.has('step3.terms')">
                                {{ errors.first('step3.terms') }}
                            </p>
                        </div>
                    </div>
                </tab>
                <tab name="Step 8" info="Confirmation" num="8">
                    <div id="form-step-8">
                        <div class="field">
                            <label class="label">Where did you hear about us?</label>
                            <div class="control">
                                <div class="select" name="reference">
                                    <select v-model="formData.reference" v-validate="'required'" name="reference"
                                            data-vv-scope="step3">
                                        <option value="">Select</option>
                                        <option value="newspaper">Newspaper</option>
                                        <option value="social-media">Social Media</option>
                                        <option value="other">Other</option>
                                    </select>
                                </div>
                            </div>
                            <p class="help is-danger" v-show="errors.has('step3.reference')">
                                {{ errors.first('step3.reference') }}
                            </p>
                        </div>
                        <div class="field">
                            <div class="control">
                                <label class="checkbox">
                                    <input type="checkbox" name="terms" v-model="formData.terms" data-vv-scope="step3"
                                           v-validate="'required'">
                                    I agree to the <a href="#">terms and conditions</a>
                                </label>
                            </div>
                            <p class="help is-danger" v-show="errors.has('step3.terms')">
                                {{ errors.first('step3.terms') }}
                            </p>
                        </div>
                    </div>
                </tab>
            </template>
        </form-wizard>

    </div>
</template>

<script>
    import Vue from 'vue';
    import VeeValidate from 'vee-validate';
    import FormWizard from './components/FormWizard.vue';
    import Tab from './components/Tab.vue';
    import 'bulma/css/bulma.css'

    Vue.use(VeeValidate);

    export default {
        name: 'app',
        components: {
            FormWizard, Tab
        },
    }
</script>

<style lang="scss">

    @import "./../node_modules/bulma/bulma.sass";
    @import "./../node_modules/bulma-steps-component/bulma-steps.sass";

    body {
        padding: 30px;
    }

    [v-cloak] {
        display: none;
    }
</style>
