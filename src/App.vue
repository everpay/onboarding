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
                                <textarea class="textarea" name="enemy forces" v-model="formData.enemy1"
                                          placeholder="Identify enemy forces and appraise their general capabilities. Describe the enemy’s composition, disposition, location, strength, and probable courses of action. Identify adversaries and known or potential terrorist threats within the area of operations. Refer to Annex B (Intelligence) as required."
                                          v-validate="'required'" data-vv-scope="step2"></textarea>
                                <p class="help is-danger" v-show="errors.has('step2.enemy forces')">
                                    {{ errors.first('step2.enemy forces') }}
                                </p>
                            </div>
                        </div>
                        <div class="field">
                            <label class="label">Higher Headquarters Two Levels Up</label>
                            <div class="control">
                                <textarea class="input" name="hhq2" v-model="formData.friendly1"
                                          placeholder="Identify the higher headquarters two echelons above (for example, Joint Task Force-18)."
                                          v-validate="'required'" data-vv-scope="step2"></textarea>
                                <p class="help is-danger" v-show="errors.has('step2.hhq2')">
                                    {{ errors.first('step2.hhq2') }}
                                </p>
                            </div>
                        </div>
                        <div class="field">
                            <label class="label">Mission</label>
                            <div class="control">
                                <textarea class="input" name="hhq2 mission" v-model="formData.friendly2"
                                          placeholder="Input Higher Headquarters Two Levels Up Mission"
                                          v-validate="'required'" data-vv-scope="step2"></textarea>
                                <p class="help is-danger" v-show="errors.has('step2.hhq2 mission')">
                                    {{ errors.first('step2.hhq2 mission') }}
                                </p>
                            </div>
                        </div>
                        <div class="field">
                            <label class="label">Commanders Intent</label>
                            <div class="control">
                                <textarea class="input" name="hhq2 intent" v-model="formData.friendly3"
                                          placeholder="Input Higher Headquarters Two Levels Up Commanders Intent"
                                          v-validate="'required'" data-vv-scope="step2"></textarea>
                                <p class="help is-danger" v-show="errors.has('step2.hhq2 intent')">
                                    {{ errors.first('step2.hhq2 intent') }}
                                </p>
                            </div>
                        </div>
                        <div class="field">
                            <label class="label">Higher Headquarters</label>
                            <div class="control">
                                <textarea class="input" name="hhq" v-model="formData.friendly4"
                                          placeholder="Identify the higher headquarters one echelon above (for example, 1st [U.S.] Armored Division)"
                                          v-validate="'required'" data-vv-scope="step2"></textarea>
                                <p class="help is-danger" v-show="errors.has('step2.hhq')">
                                    {{ errors.first('step2.hhq') }}
                                </p>
                            </div>
                        </div>
                        <div class="field">
                            <label class="label">Mission</label>
                            <div class="control">
                                <textarea class="input" name="hhq mission" v-model="formData.friendly5"
                                          placeholder="Input Higher Headquarters Mission."
                                          v-validate="'required'" data-vv-scope="step2"></textarea>
                                <p class="help is-danger" v-show="errors.has('step2.hhq mission')">
                                    {{ errors.first('step2.hhq mission') }}
                                </p>
                            </div>
                        </div>
                        <div class="field">
                            <label class="label">Commanders Intent</label>
                            <div class="control">
                                <textarea class="input" name="hhq intent" v-model="formData.friendly6"
                                          placeholder="Input Higher Headquarters Commanders Intent"
                                          v-validate="'required'" data-vv-scope="step2"></textarea>
                                <p class="help is-danger" v-show="errors.has('step2.hhq intent')">
                                    {{ errors.first('step2.hhq intent') }}
                                </p>
                            </div>
                        </div>
                        <div class="field">
                            <label class="label">Missions of Adjacent Units</label>
                            <div class="control">
                                <textarea class="textarea" name="adjacent units" v-model="formData.friendly7"
                                          placeholder="Identify and state the missions of adjacent units and other units whose actions have a significant impact on the issuing headquarters."
                                          v-validate="'required'" data-vv-scope="step2"></textarea>
                                <p class="help is-danger" v-show="errors.has('step2.adjacent units')">
                                    {{ errors.first('step2.adjacent units') }}
                                </p>
                            </div>
                        </div>
                        <div class="field">
                            <label class="label">Interagency, Intergovernmental, and Nongovernmental Organizations</label>
                            <div class="control">
                                <textarea class="textarea" name="interagency" v-model="formData.friendly8"
                                          placeholder="dentify and state the objective or goals and primary tasks of those non-Department of Defense organizations that have a significant role within the area of operations. Refer to Annex V (Interagency Coordination) as required."
                                          v-validate="'required'" data-vv-scope="step2"></textarea>
                                <p class="help is-danger" v-show="errors.has('step2.interagency')">
                                    {{ errors.first('step2.interagency') }}
                                </p>
                            </div>
                        </div>
                        <div class="field">
                            <label class="label">Civil Considerations</label>
                            <div class="control">
                                <textarea class="textarea" name="civil considerations" v-model="formData.friendly9"
                                          placeholder="Describe the critical aspects of the civil situation that impact operations. Refer to Appendix 1 (Intelligence Estimate) to Annex B (Intelligence) as required."
                                          v-validate="'required'" data-vv-scope="step2"></textarea>
                                <p class="help is-danger" v-show="errors.has('step2.civil considerations')">
                                    {{ errors.first('step2.civil considerations') }}
                                </p>
                            </div>
                        </div>
                        <div class="field">
                            <label class="label">Attachments and Detachments</label>
                            <div class="control">
                                <textarea class="textarea" name="attachments and detachments" v-model="formData.friendly10"
                                          placeholder="List units attached to or detached from the issuing headquarters. State when each attachment or detachment is effective (for example, on order, on commitment of the reserve) if different from the effective time of the OPLAN or OPORD. Do not repeat information already listed in Annex A (Task Organization)."
                                          v-validate="'required'" data-vv-scope="step2"></textarea>
                                <p class="help is-danger" v-show="errors.has('step2.attachments and detachments')">
                                    {{ errors.first('step2.attachments and detachments') }}
                                </p>
                            </div>
                        </div>
                        <div class="field">
                            <label class="label">Assumptions</label>
                            <div class="control">
                                <textarea class="textarea" name="assumptions" v-model="formData.friendly11"
                                          placeholder="List assumptions used in the development of the OPLAN or OPORD."
                                          v-validate="'required'" data-vv-scope="step2"></textarea>
                                <p class="help is-danger" v-show="errors.has('step2.assumptions')">
                                    {{ errors.first('step2.assumptions') }}
                                </p>
                            </div>
                        </div>
                    </div>
                </tab>
                
                <tab name="Step 3" info="Mission" data-vv-scope="step3" num="3">
                    <div id="form-step-3">
                        <div class="field">
                            <label class="label">Mission</label>
                            <div class="control">
                                <textarea class="textarea" name="mission paragraph" v-model="formData.mission1"
                                          placeholder="State the unit’s mission— a short description of the who, what (task), when, where, and why (purpose) that clearly indicates the action to be taken and the reason for doing so."
                                          v-validate="'required'" data-vv-scope="step3"></textarea>
                                <p class="help is-danger" v-show="errors.has('step3.mission paragraph')">
                                    {{ errors.first('step3.mission paragraph') }}
                                </p>
                            </div>
                        </div>
                    </div>
                </tab>

                <tab name="Step 4" info="Execution" data-vv-scope="step4" num="4">
                    <div id="form-step-4">
                        <div class="field">
                            <label class="label">Commanders Intent</label>
                            <div class="control">
                                <textarea class="input" name="commanders intent" v-model="formData.execution1"
                                          placeholder="Input Commanders Intent. Consider purpose, key tasks and end state."
                                          v-validate="'required'" data-vv-scope="step4"></textarea>
                                <p class="help is-danger" v-show="errors.has('step4.commanders intent')">
                                    {{ errors.first('step4.commanders intent') }}
                                </p>
                            </div>
                        </div>
                    </div>
                    <div class="field">
                            <label class="label">Concept of Operations</label>
                            <div class="control">
                                <textarea class="textarea" name="concept of operations" v-model="formData.execution2"
                                          placeholder="The concept of operations is a statement that directs the manner in which subordinate units cooperate to accomplish the mission and establishes the sequence of actions the force will use to achieve the end state."
                                          v-validate="'required'" data-vv-scope="step4"></textarea>
                                <p class="help is-danger" v-show="errors.has('step4.concept of operations')">
                                    {{ errors.first('step4.concept of operations') }}
                                </p>
                            </div>
                    </div>
                    <div class="field">
                            <label class="label">Scheme of Movement and Maneuver</label>
                            <div class="control">
                                <textarea class="textarea" name="scheme of maneuver" v-model="formData.execution3"
                                          placeholder="The scheme of maneuver is a statement that directs the manner in which subordinate units cooperate to accomplish the mission and establishes the sequence of actions the force will use to achieve the end state."
                                          v-validate="'required'" data-vv-scope="step4"></textarea>
                                <p class="help is-danger" v-show="errors.has('step4.scheme of maneuver')">
                                    {{ errors.first('step4.scheme of maneuver') }}
                                </p>
                            </div>
                    </div>
                    <div class="field">
                            <label class="label">Phase One</label>
                            <div class="control">
                                <textarea class="textarea" name="phase one" v-model="formData.execution4"
                                          placeholder="Enter phase details. Consider starting state, key tasks and end state."
                                          v-validate="'required'" data-vv-scope="step4"></textarea>
                                <p class="help is-danger" v-show="errors.has('step4.phase one')">
                                    {{ errors.first('step4.phase one') }}
                                </p>
                            </div>
                    </div>
                    <div class="field">
                            <label class="label">Phase Two</label>
                            <div class="control">
                                <textarea class="textarea" name="phase two" v-model="formData.execution5"
                                          placeholder="Enter phase details. Consider starting state, key tasks and end state."
                                          v-validate="'required'" data-vv-scope="step4"></textarea>
                                <p class="help is-danger" v-show="errors.has('step4.phase two')">
                                    {{ errors.first('step4.phase two') }}
                                </p>
                            </div>
                    </div>
                    <div class="field">
                            <label class="label">Phase Three</label>
                            <div class="control">
                                <textarea class="textarea" name="phase three" v-model="formData.execution6"
                                          placeholder="Enter phase details. Consider starting state, key tasks and end state."
                                          v-validate="'required'" data-vv-scope="step4"></textarea>
                                <p class="help is-danger" v-show="errors.has('step4.phase three')">
                                    {{ errors.first('step4.phase three') }}
                                </p>
                            </div>
                    </div>
                    <div class="field">
                            <label class="label">Stability Tasks</label>
                            <div class="control">
                                <textarea class="textarea" name="stability tasks" v-model="formData.execution7"
                                          placeholder="Describe how stability tasks support the concept of operations."
                                          v-validate="'required'" data-vv-scope="step4"></textarea>
                                <p class="help is-danger" v-show="errors.has('step4.stability tasks')">
                                    {{ errors.first('step4.stability tasks') }}
                                </p>
                            </div>
                    </div>
                    <div class="field">
                            <label class="label">Tasks to Suboordinate Units</label>
                            <div class="control">
                                <textarea class="textarea" name="suboordinate unit tasks" v-model="formData.execution8"
                                          placeholder="State tasks assigned to each unit that reports directly to the headquarters issuing the order."
                                          v-validate="'required'" data-vv-scope="step4"></textarea>
                                <p class="help is-danger" v-show="errors.has('step4.suboordinate unit tasks')">
                                    {{ errors.first('step4.suboordinate unit tasks') }}
                                </p>
                            </div>
                    </div>
                        
                </tab>

                <tab name="Step 5" info="Sustainment" data-vv-scope="step5" num="5">
                    <div id="form-step-5">
                        <div class="field">
                            <label class="label">Sustainment</label>
                            <div class="control">
                                <textarea class="textarea" name="sustainment information" v-model="formData.sustainment1"
                                          placeholder="Describe the concept of sustainment, including priorities of sustainment by unit or area."
                                          v-validate="'required'" data-vv-scope="step5"></textarea>
                                <p class="help is-danger" v-show="errors.has('step5.sustainment information')">
                                    {{ errors.first('step5.sustainment information') }}
                                </p>
                            </div>
                        </div>
                    </div>
                    <div class="field">
                        <label class="label">Logistics</label>
                        <div class="control">
                            <textarea class="input" name="logistics" v-model="formData.sustainment2"
                                placeholder="Refer to Annex F (Sustainment) as required."
                                v-validate="'required'" data-vv-scope="step5"></textarea>
                                <p class="help is-danger" v-show="errors.has('step5.logistics')">
                                    {{ errors.first('step5.logistics') }}
                                </p>
                        </div>
                    </div>
                    <div class="field">
                        <label class="label">Personnel</label>
                        <div class="control">
                            <textarea class="input" name="personnel" v-model="formData.sustainment3"
                                placeholder="Refer to Annex F (Sustainment) as required."
                                v-validate="'required'" data-vv-scope="step5"></textarea>
                                <p class="help is-danger" v-show="errors.has('step5.personnel')">
                                    {{ errors.first('step5.personnel') }}
                                </p>
                        </div>
                    </div>
                    <div class="field">
                        <label class="label">Health Service Support</label>
                        <div class="control">
                            <textarea class="input" name="health service support" v-model="formData.sustainment4"
                                placeholder="Refer to Annex F (Sustainment) as required."
                                v-validate="'required'" data-vv-scope="step5"></textarea>
                                <p class="help is-danger" v-show="errors.has('step5.health service support')">
                                    {{ errors.first('step5.health service support') }}
                                </p>
                        </div>
                    </div>
                </tab>
                <tab name="Step 6" info="Command & Signal" data-vv-scope="step6" num="6">
                    <div id="form-step-6">
                        <div class="field">
                            <label class="label">Location of Commander and Key Leaders</label>
                            <div class="control">
                            <textarea class="textarea" name="commander location" v-model="formData.commandAndSignal1"
                                placeholder="State where the commander and key leaders intend to be during the operation, by phase if the operation is phased.."
                                v-validate="'required'" data-vv-scope="step6"></textarea>
                                <p class="help is-danger" v-show="errors.has('step6.commander location')">
                                    {{ errors.first('step6.commander location') }}
                                </p>
                            </div>
                        </div>
                        <div class="field">
                            <label class="label">Succession of Command</label>
                            <div class="control">
                            <textarea class="textarea" name="command succession" v-model="formData.commandAndSignal2"
                                placeholder="State where the commander and key leaders intend to be during the operation, by phase if the operation is phased.."
                                v-validate="'required'" data-vv-scope="step6"></textarea>
                                <p class="help is-danger" v-show="errors.has('step6.command succession')">
                                    {{ errors.first('step6.command succession') }}
                                </p>
                            </div>
                        </div>
                        <div class="field">
                            <label class="label">Liason Requirments</label>
                            <div class="control">
                            <textarea class="textarea" name="liason requirements" v-model="formData.commandAndSignal3"
                                placeholder="State where the commander and key leaders intend to be during the operation, by phase if the operation is phased.."
                                v-validate="'required'" data-vv-scope="step6"></textarea>
                                <p class="help is-danger" v-show="errors.has('step6.liason requirements')">
                                    {{ errors.first('step6.liason requirements') }}
                                </p>
                            </div>
                        </div>
                        <div class="field">
                            <label class="label">Command Posts</label>
                            <div class="control">
                            <textarea class="textarea" name="command posts" v-model="formData.commandAndSignal4"
                                placeholder="State where the commander and key leaders intend to be during the operation, by phase if the operation is phased.."
                                v-validate="'required'" data-vv-scope="step6"></textarea>
                                <p class="help is-danger" v-show="errors.has('step6.command posts')">
                                    {{ errors.first('step6.command posts') }}
                                </p>
                            </div>
                        </div>
                        <div class="field">
                            <label class="label">Reports</label>
                            <div class="control">
                            <textarea class="textarea" name="reports" v-model="formData.commandAndSignal5"
                                placeholder="State where the commander and key leaders intend to be during the operation, by phase if the operation is phased.."
                                v-validate="'required'" data-vv-scope="step6"></textarea>
                                <p class="help is-danger" v-show="errors.has('step6.reports')">
                                    {{ errors.first('step6.reports') }}
                                </p>
                            </div>
                        </div>
                        <div class="field">
                            <label class="label">Signal</label>
                            <div class="control">
                            <textarea class="textarea" name="signal" v-model="formData.commandAndSignal6"
                                placeholder="State where the commander and key leaders intend to be during the operation, by phase if the operation is phased.."
                                v-validate="'required'" data-vv-scope="step6"></textarea>
                                <p class="help is-danger" v-show="errors.has('step6.signal')">
                                    {{ errors.first('step6.signal') }}
                                </p>
                            </div>
                        </div>
                </div>
                </tab>
                <tab name="Step 7" info="Attachments" data-vv-scope="step7" num="7">
                    <div id="form-step-7">
                        // TAB 7 THINGS
                    </div>
                </tab>
                <tab name="Step 8" info="Confirmation" data-vv-scope="step8" num="8">
                    <div id="form-step-8">
                        // TAB 8 THINGS    
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
