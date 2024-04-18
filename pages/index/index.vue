<template>
	<view class="content">
		<view class="title">默认状态</view>
		<view class="item">
			<uni-list>
				<uni-list-item title="所在地区" :right-text="addressStr" show-arrow
					@click.native="addressPopup=true"></uni-list-item>
			</uni-list>
		</view>

		<view class="title">回显</view>
		<view class="item">
			<uni-list>
				<uni-list-item title="所在地区" :right-text="addressStr2" show-arrow
					@click.native="addressPopup2=true"></uni-list-item>
			</uni-list>
		</view>
		<sx-address-picker v-model="addressPopup" @confirm="addressConfirm($event, 'formData')" />

		<sx-address-picker v-model="addressPopup2" @confirm="addressConfirm($event, 'formData2')"
			:selected="selectedAddress"></sx-address-picker>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				addressPopup: false,
				addressPopup2: false,
				selectedAddress: [],
				formData: {
					country: '',
					province: '',
					city: '',
					area: '',
					street: ''
				},
				formData2: {
					country: '埃及',
					// province: "上海市",
					// city: "市辖区",
					// area: "徐汇区",
					// street: "天平路街道"
				}
			}
		},
		onLoad() {
			this.addressChange()
		},
		methods: {
			addressConfirm(address, key) {
				const [country, province, city, area, street] = address
				this.address = province ? address.filter((v, i) => i > 0) : address;
				if (address.length === 5) {
					this[key].country = country.name
					this[key].province = province.name
					this[key].city = city.name
					this[key].area = area.name
					this[key].street = street.name
				} else {
					this[key].country = country.name
					this[key].province = undefined
					this[key].city = undefined
					this[key].area = undefined
					this[key].street = undefined
				}
				this.addressChange()
			},
			addressChange() {
				const {
					country,
					province,
					city,
					area,
					street
				} = this.formData2

				this.selectedAddress = province ? [country,
					province,
					city,
					area,
					street
				] : [country]
			}
		},
		computed: {
			addressStr() {
				const {
					country,
					province,
					city,
					area,
					street
				} = this.formData
				return country ? `${country || ''} ${province ||''} ${city ||''} ${area || ''} ${street || ''}` :
					'省 市 区 街道'
			},
			addressStr2() {
				const {
					country,
					province,
					city,
					area,
					street
				} = this.formData2
				return country ? `${country || ''} ${province ||''} ${city ||''} ${area || ''} ${street || ''}` :
					'省 市 区 街道'
			}
		}
	}
</script>

<style>
	.content {
		padding: 10px;
	}

	.title {
		font-size: 14px;
		font-weight: bold;
		margin-bottom: 10px;
	}

	.item {
		margin-bottom: 20px;
	}
</style>