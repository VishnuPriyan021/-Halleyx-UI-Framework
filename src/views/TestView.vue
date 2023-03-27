<template>
  <div>
    <MongoDBRecord :data="record" :show="true"/>
  </div>
</template>

<script>
import MongoDBRecord from '../components/MongoDBRecord.vue'

export default {
  components: {
    MongoDBRecord
  },
  data () {
    return {
      record: {
        quote: {
          quoteItem: [
            {
              id: '1',
              state: 'approved',
              action: 'add',
              quantity: '11',
              unitPrice: 1000,
              '@type': 'QuoteItem',
              attachment: [
                {
                  description: 'TMF Tariff Plan',
                  href: 'http://hostname:port/documentManagement/attachment/22',
                  id: '22',
                  type: 'Document',
                  url: 'http://xxxxx',
                  founded: 'not found'
                }
              ],
              appointment: [
                {
                  href: 'http://hostname:port/appointmentManagement/appointment/111',
                  id: '111',
                  description: 'This  appointment to present advantage of solution ',
                  founded: 'not found'
                }
              ],
              productOffering: {
                id: '5295',
                href: 'https://host:port/productOffering/productOffering/5295',
                name: 'TMF Tariff plan ',
                '@type': 'TMFTariffPlanPO',
                founded: 'not found',
                productOffering: 'therila'
              },
              quoteItemPrice: [
                {
                  priceType: 'recurring',
                  recurringChargePeriod: 'monthly',
                  name: 'TMFTPM',
                  description: 'Recurring fee for TMF',
                  '@type': 'QuoteItemPrice',
                  priceAlteration: [
                    {
                      name: 'Corporate Discount',
                      description: 'This  price alteration ...',
                      priceType: 'Recurring',
                      recurringChargePeriod: 'monthly',
                      priority: 1,
                      priceCondition: 'Only applicable if 10 or more ordered',
                      '@type': 'PriceAlteration',
                      price: {
                        percentage: 10
                      }
                    }
                  ],
                  price: {
                    taxIncludedAmount: 10000,
                    dutyFreeAmount: '30',
                    taxRate: 20
                  }
                }
              ],
              product: {
                name: 'TMF Tariff plan',
                characteristic: [
                  {
                    name: 'Voice Bundle',
                    value: 'Illimited'
                  },
                  {
                    name: 'Data Bundle',
                    value: '32 GB/month'
                  }
                ],
                productSpecification: {
                  id: '2489',
                  href: 'https://host:port/productSpecification/productSpecification/2489',
                  version: '1.5',
                  name: 'RTMFPlan',
                  '@type': 'ProductSpec',
                  founded: 'not found'
                }
              }
            },
            {
              id: '2',
              state: 'approved',
              action: 'add',
              quantity: '10',
              unitPrice: '',
              '@type': ' QuoteItem...',
              productOffering: {
                id: '63',
                href: 'https://host:port/productOffering/productOffering/63',
                name: 'Nice Handset',
                '@type': 'Handset',
                founded: 'not found'
              },
              quoteItemPrice: [
                {
                  priceType: 'oneOff',
                  name: 'Nice Phone',
                  description: 'This  quote price ...',
                  price: {
                    taxIncludedAmount: 0,
                    dutyFreeAmount: '400',
                    taxRate: 20
                  }
                }
              ],
              product: {
                name: 'Nice Phone',
                characteristic: [
                  {
                    name: 'Colour',
                    value: 'black'
                  },
                  {
                    name: 'Memory',
                    value: '32'
                  }
                ],
                productSpecification: {
                  id: '9',
                  href: 'https://host:port/productSpecification/productSpecification/9',
                  version: '3.0',
                  name: 'NicePhone',
                  '@type': 'ProductSpec',
                  founded: 'not found'
                }
              }
            },
            {
              id: '3',
              state: 'approved',
              action: 'add',
              quantity: 1,
              unitPrice: '',
              productOffering: {
                id: '85',
                href: 'https://host:port/productOffering/productOffering/85',
                name: '24/7/7 Support',
                founded: 'not found'
              },
              quoteItemPrice: [
                {
                  priceType: 'recurring',
                  recurringChargePeriod: 'monthly',
                  name: '247 Support',
                  description: 'This  quote price ...',
                  priceAlteration: [
                    {
                      name: 'Discount',
                      description: 'This  price alteration ...',
                      priceType: 'recurring',
                      recurringChargePeriod: 'monthly',
                      applicationDuration: 12,
                      priority: 1,
                      priceCondition: 'free support 12 first months',
                      price: {
                        percentage: 100
                      }
                    }
                  ],
                  price: {
                    taxIncludedAmount: 0,
                    dutyFreeAmount: '20',
                    taxRate: 20
                  }
                }
              ],
              product: {
                name: 'Silver Support',
                characteristic: [
                  [
                    {
                      name: 'Time to respond',
                      value: '4H'
                    }
                  ]
                ],
                productSpecification: {
                  id: '289',
                  href: 'https://host:port/productSpecification/productSpecification/289',
                  version: '1.5',
                  name: 'Support',
                  '@type': 'ProductSpec',
                  founded: 'not found'
                }
              }
            }
          ],
          quoteTotalPrice: 0
        }
      }
    }
  }
}
</script>
