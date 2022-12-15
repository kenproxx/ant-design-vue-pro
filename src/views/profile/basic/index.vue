<template>
  <page-header-wrapper>
    <a-card :bordered="false">
      <a-descriptions title="Thông tin cá nhân">
        <a-descriptions-item label="Tên thánh">1000000000</a-descriptions-item>
        <a-descriptions-item label="Tên gọi">3214321432</a-descriptions-item>
        <a-descriptions-item label="Ngày tháng năm sinh">已取货</a-descriptions-item>
        <a-descriptions-item label="Số điện thoại">1234123421</a-descriptions-item>
        <a-descriptions-item label="Email">1234123421</a-descriptions-item>
      </a-descriptions>
      <a-divider style="margin-bottom: 32px"/>
      <a-descriptions title="Thông tin chi tiết">
        <a-descriptions-item label="Ngày bổn mạng">	无</a-descriptions-item>
        <a-descriptions-item label="Ngày rửa tội">付小小</a-descriptions-item>
        <a-descriptions-item label="Người rửa tội">18100000000</a-descriptions-item>
        <a-descriptions-item label="Ngày thêm sức">菜鸟仓储</a-descriptions-item>
        <a-descriptions-item label="Người thêm sức">浙江省杭州市西湖区万塘路18号</a-descriptions-item>
      </a-descriptions>
      <a-divider style="margin-bottom: 32px"/>
      <a-descriptions title="Thông tin liên hệ">
        <a-descriptions-item label="Tên thánh bố">	无</a-descriptions-item>
        <a-descriptions-item label="Tên gọi bố">	无</a-descriptions-item>
        <a-descriptions-item label="Số điện thoại bố">付小小</a-descriptions-item>
        <a-descriptions-item label="Tên thánh mẹ">18100000000</a-descriptions-item>
        <a-descriptions-item label="Tên gọi mẹ">18100000000</a-descriptions-item>
        <a-descriptions-item label="Số điện thoại mẹ">菜鸟仓储</a-descriptions-item>
        <a-descriptions-item label="Thuộc">浙江省杭州市西湖区万塘路18号</a-descriptions-item>
        <a-descriptions-item label="Địa chỉ">浙江省杭州市西湖区万塘路18号</a-descriptions-item>
      </a-descriptions>
      <a-divider style="margin-bottom: 32px"/>

<!--  Tình trạng học tập - Sẽ update-->
<!--      <div class="title">Tình trạng học tập</div>-->
<!--      <s-table-->
<!--        style="margin-bottom: 24px"-->
<!--        row-key="key"-->
<!--        :columns="scheduleColumns"-->
<!--        :data="loadScheduleData">-->

<!--        <template-->
<!--          slot="status"-->
<!--          slot-scope="status">-->
<!--          <a-badge :status="status" :text="status | statusFilter"/>-->
<!--        </template>-->

<!--      </s-table>-->

    </a-card>
  </page-header-wrapper>
</template>

<script>
import { STable } from '@/components'

export default {
  components: {
    STable
  },
  data () {
    return {
      goodsColumns: [
        {
          title: '商品编号',
          dataIndex: 'id',
          key: 'id'
        },
        {
          title: '商品名称',
          dataIndex: 'name',
          key: 'name'
        },
        {
          title: '商品条码',
          dataIndex: 'barcode',
          key: 'barcode'
        },
        {
          title: '单价',
          dataIndex: 'price',
          key: 'price',
          align: 'right'
        },
        {
          title: '数量（件）',
          dataIndex: 'num',
          key: 'num',
          align: 'right'
        },
        {
          title: '金额',
          dataIndex: 'amount',
          key: 'amount',
          align: 'right'
        }
      ],
      // 加载数据方法 必须为 Promise 对象
      loadGoodsData: () => {
        return new Promise(resolve => {
          resolve({
            data: [
              {
                id: '1234561',
                name: '矿泉水 550ml',
                barcode: '12421432143214321',
                price: '2.00',
                num: '1',
                amount: '2.00'
              },
              {
                id: '1234562',
                name: '凉茶 300ml',
                barcode: '12421432143214322',
                price: '3.00',
                num: '2',
                amount: '6.00'
              },
              {
                id: '1234563',
                name: '好吃的薯片',
                barcode: '12421432143214323',
                price: '7.00',
                num: '4',
                amount: '28.00'
              },
              {
                id: '1234564',
                name: '特别好吃的蛋卷',
                barcode: '12421432143214324',
                price: '8.50',
                num: '3',
                amount: '25.50'
              }
            ],
            pageSize: 10,
            pageNo: 1,
            totalPage: 1,
            totalCount: 10
          })
        }).then(res => {
          return res
        })
      },

      scheduleColumns: [
        {
          title: '时间',
          dataIndex: 'time',
          key: 'time'
        },
        {
          title: '当前进度',
          dataIndex: 'rate',
          key: 'rate'
        },
        {
          title: '状态',
          dataIndex: 'status',
          key: 'status',
          scopedSlots: { customRender: 'status' }
        },
        {
          title: '操作员ID',
          dataIndex: 'operator',
          key: 'operator'
        },
        {
          title: '耗时',
          dataIndex: 'cost',
          key: 'cost'
        }
      ],
      loadScheduleData: () => {
        return new Promise(resolve => {
          resolve({
            data: [
              {
                key: '1',
                time: '2017-10-01 14:10',
                rate: '联系客户',
                status: 'processing',
                operator: '取货员 ID1234',
                cost: '5mins'
              },
              {
                key: '2',
                time: '2017-10-01 14:05',
                rate: '取货员出发',
                status: 'success',
                operator: '取货员 ID1234',
                cost: '1h'
              },
              {
                key: '3',
                time: '2017-10-01 13:05',
                rate: '取货员接单',
                status: 'success',
                operator: '取货员 ID1234',
                cost: '5mins'
              },
              {
                key: '4',
                time: '2017-10-01 13:00',
                rate: '申请审批通过',
                status: 'success',
                operator: '系统',
                cost: '1h'
              },
              {
                key: '5',
                time: '2017-10-01 12:00',
                rate: '发起退货申请',
                status: 'success',
                operator: '用户',
                cost: '5mins'
              }
            ],
            pageSize: 10,
            pageNo: 1,
            totalPage: 1,
            totalCount: 10
          })
        }).then(res => {
          return res
        })
      }
    }
  },
  filters: {
    statusFilter (status) {
      const statusMap = {
        'processing': '进行中',
        'success': '完成',
        'failed': '失败'
      }
      return statusMap[status]
    }
  },
  computed: {
    title () {
      return this.$route.meta.title
    }
  }

}
</script>

<style lang="less" scoped>
  .title {
    color: rgba(0,0,0,.85);
    font-size: 16px;
    font-weight: 500;
    margin-bottom: 16px;
  }
</style>
