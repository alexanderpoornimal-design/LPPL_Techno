<!-- 
	Add Awards - Page to create awards with criteria
 -->

<template>
	<div>
		<!-- Page Header -->
		<div class="page-header">
			<h1>Create New Award</h1>
			<p>Set up new awards with marking criteria</p>
		</div>

		<a-row :gutter="24">
			<a-col :span="24" :lg="16">
				<a-card title="Award Information" class="mb-24">
					<a-form
						:form="form"
						@submit="handleSubmit"
						layout="vertical"
					>
						<a-form-item label="Award Category">
							<a-input
								v-decorator="[
									'awardCategory',
									{
										rules: [{ required: true, message: 'Please input award category!' }]
									}
								]"
								placeholder="Enter award category"
							/>
						</a-form-item>

						<a-form-item label="Award Description">
							<a-textarea
								v-decorator="[
									'awardDescription',
									{
										rules: [{ required: true, message: 'Please input award description!' }]
									}
								]"
								placeholder="Enter detailed description of the award"
								:rows="4"
							/>
						</a-form-item>

						<a-form-item label="Total Marks">
							<a-input-number
								v-decorator="[
									'totalMarks',
									{
										rules: [{ required: true, message: 'Please input total marks!' }]
									}
								]"
								placeholder="Enter total marks"
								style="width: 100%"
								:min="1"
								:max="1000"
							/>
						</a-form-item>
					</a-form>
				</a-card>

				<!-- Marking Criteria Section -->
				<a-card title="Marking Criteria" class="mb-24">
					<div class="criteria-section">
						<div class="criteria-header">
							<h3>Evaluation Criteria</h3>
							<p>Define the criteria and allocated marks for this award</p>
						</div>

						<div v-for="(criterion, index) in criteria" :key="index" class="criterion-item">
							<a-row :gutter="16" align="middle">
								<a-col :span="16">
									<a-input
										v-model="criterion.name"
										placeholder="Enter criteria name"
										size="large"
									/>
								</a-col>
								<a-col :span="6">
									<a-input-number
										v-model="criterion.marks"
										placeholder="Marks"
										style="width: 100%"
										:min="1"
										:max="1000"
									/>
								</a-col>
								<a-col :span="2">
									<a-button
										type="danger"
										icon="delete"
										@click="removeCriterion(index)"
										:disabled="criteria.length === 1"
									/>
								</a-col>
							</a-row>
						</div>

						<div class="criteria-actions">
							<a-button type="dashed" @click="addCriterion" icon="plus" size="large">
								Add More Criteria
							</a-button>
						</div>

						<div class="criteria-summary" v-if="criteria.length > 0">
							<a-alert
								:message="`Total Allocated Marks: ${totalAllocatedMarks}`"
								:type="totalAllocatedMarks === form.getFieldValue('totalMarks') ? 'success' : 'warning'"
								show-icon
							/>
						</div>
					</div>
				</a-card>

				<a-form-item>
					<a-button type="primary" html-type="submit" :loading="loading" size="large">
						Create Award
					</a-button>
					<a-button style="margin-left: 8px;" @click="resetForm" size="large">
						Reset
					</a-button>
				</a-form-item>
			</a-col>

			<a-col :span="24" :lg="8">
				<a-card title="Recent Awards" class="mb-24">
					<a-list :data-source="recentAwards" size="small">
						<a-list-item slot="renderItem" slot-scope="item">
							<a-list-item-meta>
								<a slot="title">{{ item.name }}</a>
								<template slot="description">
									{{ item.category }} • {{ item.totalMarks }} marks
								</template>
							</a-list-item-meta>
							<template slot="actions">
								<a-tag :color="getCategoryColor(item.category)">{{ item.category }}</a-tag>
							</template>
						</a-list-item>
					</a-list>
				</a-card>

				<a-card title="Award Statistics">
					<a-row :gutter="16">
						<a-col :span="12">
							<div class="stat-item">
								<div class="stat-value">{{ awardStats.total }}</div>
								<div class="stat-label">Total Awards</div>
							</div>
						</a-col>
						<a-col :span="12">
							<div class="stat-item">
								<div class="stat-value">{{ awardStats.active }}</div>
								<div class="stat-label">Active</div>
							</div>
						</a-col>
					</a-row>
					<a-row :gutter="16" style="margin-top: 16px;">
						<a-col :span="12">
							<div class="stat-item">
								<div class="stat-value">{{ awardStats.completed }}</div>
								<div class="stat-label">Completed</div>
							</div>
						</a-col>
						<a-col :span="12">
							<div class="stat-item">
								<div class="stat-value">{{ awardStats.pending }}</div>
								<div class="stat-label">Pending</div>
							</div>
						</a-col>
					</a-row>
				</a-card>
			</a-col>
		</a-row>
	</div>
</template>

<script>
	export default ({
		data() {
			return {
				form: this.$form.createForm(this),
				loading: false,
				criteria: [
					{
						name: '',
						marks: null
					}
				],
				recentAwards: [
					{
						name: 'Excellence in Innovation',
						category: 'innovation',
						totalMarks: 100
					},
					{
						name: 'Academic Achievement Award',
						category: 'academic',
						totalMarks: 150
					},
					{
						name: 'Leadership Excellence',
						category: 'leadership',
						totalMarks: 120
					},
					{
						name: 'Research Excellence',
						category: 'research',
						totalMarks: 200
					}
				],
				awardStats: {
					total: 156,
					active: 45,
					completed: 89,
					pending: 22
				}
			}
		},
		computed: {
			totalAllocatedMarks() {
				return this.criteria.reduce((total, criterion) => {
					return total + (criterion.marks || 0);
				}, 0);
			}
		},
		methods: {
			handleSubmit(e) {
				e.preventDefault();
				this.form.validateFields((err, values) => {
					if (!err) {
						// Validate criteria
						const validCriteria = this.criteria.filter(c => c.name && c.marks);
						if (validCriteria.length === 0) {
							this.$message.error('Please add at least one criterion!');
							return;
						}

						if (this.totalAllocatedMarks !== values.totalMarks) {
							this.$message.error('Total allocated marks must equal the award total marks!');
							return;
						}

						this.loading = true;
						const awardData = {
							...values,
							criteria: validCriteria
						};
						
						console.log('Award data: ', awardData);
						
						// Simulate API call
						setTimeout(() => {
							this.loading = false;
							this.$message.success('Award created successfully!');
							this.resetForm();
						}, 2000);
					}
				});
			},
			resetForm() {
				this.form.resetFields();
				this.criteria = [
					{
						name: '',
						marks: null
					}
				];
			},
			addCriterion() {
				this.criteria.push({
					name: '',
					marks: null
				});
			},
			removeCriterion(index) {
				if (this.criteria.length > 1) {
					this.criteria.splice(index, 1);
				}
			},
			getCategoryColor(category) {
				const colors = {
					academic: 'blue',
					innovation: 'green',
					leadership: 'purple',
					research: 'orange',
					community: 'cyan',
					sports: 'red',
					arts: 'magenta'
				};
				return colors[category] || 'default';
			}
		}
	})

</script>

<style lang="scss">
.page-header {
	margin-bottom: 24px;
	
	h1 {
		margin: 0;
		font-size: 24px;
		font-weight: 600;
		color: #1f2937;
	}
	
	p {
		margin: 4px 0 0 0;
		color: #6b7280;
		font-size: 14px;
	}
}

.criteria-section {
	.criteria-header {
		margin-bottom: 24px;
		
		h3 {
			margin: 0 0 8px 0;
			font-size: 18px;
			font-weight: 600;
			color: #1f2937;
		}
		
		p {
			margin: 0;
			color: #6b7280;
			font-size: 14px;
		}
	}
	
	.criterion-item {
		margin-bottom: 16px;
		padding: 16px;
		border: 1px solid #e5e7eb;
		border-radius: 8px;
		background-color: #f9fafb;
	}
	
	.criteria-actions {
		margin-top: 16px;
		text-align: center;
	}
	
	.criteria-summary {
		margin-top: 16px;
	}
}

.stat-item {
	text-align: center;
	padding: 16px 0;
	
	.stat-value {
		font-size: 24px;
		font-weight: 600;
		color: #1f2937;
		margin-bottom: 4px;
	}
	
	.stat-label {
		font-size: 12px;
		color: #6b7280;
		text-transform: uppercase;
		letter-spacing: 0.5px;
	}
}
</style>
