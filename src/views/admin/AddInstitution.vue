<!-- 
	Add Institution - Form to add new institutions
 -->

<template>
	<div>
		<!-- Page Header -->
		<div class="page-header">
			<h1>Add New Institution</h1>
			<p>Register new institutions in the system</p>
		</div>

		<a-row :gutter="24">
			<a-col :span="24" :lg="16">
				<a-card title="Institution Information" class="mb-24">
					<a-form
						:form="form"
						@submit="handleSubmit"
						layout="vertical"
					>
						<a-form-item label="Institution Name">
							<a-input
								v-decorator="[
									'institutionName',
									{
										rules: [{ required: true, message: 'Please input institution name!' }]
									}
								]"
								placeholder="Enter institution name"
							/>
						</a-form-item>

						<a-form-item label="Upload Institute Image">
							<a-upload
								v-decorator="[
									'instituteImage',
									{
										rules: [{ required: true, message: 'Please upload institute image!' }]
									}
								]"
								name="file"
								list-type="picture-card"
								class="image-uploader"
								:show-upload-list="false"
								action="https://www.mocky.io/v2/5cc8019d300000980a055e76"
								:before-upload="beforeUpload"
								@change="handleChange"
							>
								<div v-if="imageUrl">
									<img :src="imageUrl" alt="institute" style="width: 100%" />
								</div>
								<div v-else>
									<a-icon :type="loading ? 'loading' : 'plus'" />
									<div class="ant-upload-text">Upload</div>
								</div>
							</a-upload>
						</a-form-item>

						<a-form-item label="Award Category">
							<a-select
								v-decorator="[
									'awardCategory',
									{
										rules: [{ required: true, message: 'Please select award category!' }]
									}
								]"
								mode="multiple"
								placeholder="Select award categories"
								style="width: 100%"
							>
								<a-select-option value="award-14">Award No. 14 - Financial Institution of the Year for Best Digital Payment</a-select-option>
								<a-select-option value="award-6a">Award No. 6A - Most Popular Digital Payment Product - State Banks</a-select-option>
								<a-select-option value="award-6b">Award No. 6B - Most Popular Digital Payment Product - Private Banks</a-select-option>
								<a-select-option value="award-7">Award No. 7 - Best Digital Payment Innovation</a-select-option>
								<a-select-option value="award-8">Award No. 8 - Best Digital Payment Security</a-select-option>
							</a-select>
						</a-form-item>

						<a-form-item>
							<a-button type="primary" html-type="submit" :loading="loading" size="large">
								Add Institution
							</a-button>
							<a-button style="margin-left: 8px;" @click="resetForm" size="large">
								Reset
							</a-button>
						</a-form-item>
					</a-form>
				</a-card>
			</a-col>

			<a-col :span="24" :lg="8">
				<a-card title="Recent Institutions" class="mb-24">
					<a-list :data-source="recentInstitutions" size="small">
						<a-list-item slot="renderItem" slot-scope="item">
							<a-list-item-meta>
								<a slot="title">{{ item.name }}</a>
								<template slot="description">
									{{ item.type }} • {{ item.contactPerson }}
								</template>
							</a-list-item-meta>
							<template slot="actions">
								<a-tag :color="getTypeColor(item.type)">{{ item.type }}</a-tag>
							</template>
						</a-list-item>
					</a-list>
				</a-card>

				<a-card title="Institution Statistics">
					<a-row :gutter="16">
						<a-col :span="12">
							<div class="stat-item">
								<div class="stat-value">{{ institutionStats.total }}</div>
								<div class="stat-label">Total</div>
							</div>
						</a-col>
						<a-col :span="12">
							<div class="stat-item">
								<div class="stat-value">{{ institutionStats.universities }}</div>
								<div class="stat-label">Universities</div>
							</div>
						</a-col>
					</a-row>
					<a-row :gutter="16" style="margin-top: 16px;">
						<a-col :span="12">
							<div class="stat-item">
								<div class="stat-value">{{ institutionStats.colleges }}</div>
								<div class="stat-label">Colleges</div>
							</div>
						</a-col>
						<a-col :span="12">
							<div class="stat-item">
								<div class="stat-value">{{ institutionStats.schools }}</div>
								<div class="stat-label">Schools</div>
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
				imageUrl: '',
				uploadLoading: false,
				recentInstitutions: [
					{
						name: 'University of Colombo',
						type: 'university',
						contactPerson: 'Dr. John Smith'
					},
					{
						name: 'Colombo International School',
						type: 'school',
						contactPerson: 'Ms. Sarah Johnson'
					},
					{
						name: 'Sri Lanka Institute of Technology',
						type: 'college',
						contactPerson: 'Prof. Michael Brown'
					},
					{
						name: 'National Research Institute',
						type: 'research',
						contactPerson: 'Dr. Emily Davis'
					}
				],
				institutionStats: {
					total: 28,
					universities: 8,
					colleges: 12,
					schools: 6
				}
			}
		},
		methods: {
			handleSubmit(e) {
				e.preventDefault();
				this.form.validateFields((err, values) => {
					if (!err) {
						this.loading = true;
						console.log('Received values of form: ', values);
						
						// Simulate API call
						setTimeout(() => {
							this.loading = false;
							this.$message.success('Institution added successfully!');
							this.resetForm();
						}, 2000);
					}
				});
			},
			resetForm() {
				this.form.resetFields();
			},
			getTypeColor(type) {
				const colors = {
					university: 'blue',
					college: 'green',
					school: 'orange',
					research: 'purple',
					other: 'default'
				};
				return colors[type] || 'default';
			},
			beforeUpload(file) {
				const isJpgOrPng = file.type === 'image/jpeg' || file.type === 'image/png';
				if (!isJpgOrPng) {
					this.$message.error('You can only upload JPG/PNG file!');
				}
				const isLt2M = file.size / 1024 / 1024 < 2;
				if (!isLt2M) {
					this.$message.error('Image must smaller than 2MB!');
				}
				return isJpgOrPng && isLt2M;
			},
			handleChange(info) {
				if (info.file.status === 'uploading') {
					this.uploadLoading = true;
					return;
				}
				if (info.file.status === 'done') {
					// Get this url from response in real world.
					this.getBase64(info.file.originFileObj, imageUrl => {
						this.imageUrl = imageUrl;
						this.uploadLoading = false;
					});
				}
			},
			getBase64(img, callback) {
				const reader = new FileReader();
				reader.addEventListener('load', () => callback(reader.result));
				reader.readAsDataURL(img);
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
