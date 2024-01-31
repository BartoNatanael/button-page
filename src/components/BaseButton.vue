<template>
    <component
        :is="customComponent()"
        class="btn"
        :class="customClassName()"
        :disabled="disabled"
        @click="onClick"
    >
        <slot></slot>
    </component>
</template>

<script lang="tsx">
import { defineComponent, type PropType } from "vue";
import { RouterLink } from "vue-router";

type BaseButtonType = "a" | "router-link" | "button";
type BaseButtonColor = "dark-orange" | "orange" | "red" | "green" | "dark-green";
type BaseButtonSize = "small" | "regular" | "large";

export default defineComponent({
    props: {
        color: {
            type: String as PropType<BaseButtonColor>,
            default: "green"
        },
        outlined: {
            type: Boolean as PropType<boolean>,
            default: false
        },
        size: {
            type: String as PropType<BaseButtonSize>,
            default: "regular"
        },
        disabled: {
            type: Boolean as PropType<boolean>,
            default: false
        },
        component: {
            type: Object as PropType<{ type: BaseButtonType; address: string }>,
            required: false
        },
        blockDisplay: {
            type: Boolean as PropType<boolean>,
            default: false
        }
    },
    setup(props, { emit }) {
        const onClick = (event: Event) => {
            emit("click", event);
        };

        const customClassName = () => {
            let className = `btn--${props.color} btn--${props.size}`;

            if (props.outlined) {
                className += " btn--outlined";
            }

            if (props.blockDisplay) {
                className += " btn--block";
            }

            return className;
        };

        const customComponent = () => {
            if (props.component) {
                if (props.component.type === "a") {
                    return (
                        <a href={props.component.address}>
                            <slot></slot>
                        </a>
                    );
                } else if (props.component.type === "router-link") {
                    return (
                        <RouterLink to={props.component.address}>
                            <slot></slot>
                        </RouterLink>
                    );
                }
            }

            return (
                <button>
                    <slot></slot>
                </button>
            );
        };

        return { customClassName, onClick, customComponent };
    }
});
</script>

<style scoped lang="scss">
a.btn {
    display: inline-block;
    text-decoration: none;
}
.btn,
a.btn {
    color: $color-white;
    margin: auto 0;
    border: none;
    cursor: pointer;
    display: inline-block;
    white-space: nowrap;

    // sizes
    &--regular {
        border-radius: 24px;
        padding: 14px 24px;
    }

    &--small {
        border-radius: 20px;
        padding: 10px 16px;
    }

    &--large {
        border-radius: 28px;
        padding: 16px 24px;
    }

    // colors
    &--orange,
    &--orange:visited {
        background-color: $color-orange;
        color: $color-dark-green;

        &.btn--outlined {
            border-color: $color-orange;
            color: $color-orange;

            &:hover:enabled,
            &:focus:enabled,
            &:visited:hover,
            &:link:hover {
                background-color: $color-orange-outline;
            }
        }

        &:hover:enabled,
        &:focus:enabled,
        &:visited:hover,
        &:link:hover {
            background-color: $color-orange-hover;
        }
    }

    &--dark-orange,
    &--dark-orange:visited {
        background-color: $color-dark-orange;

        &.btn--outlined {
            border-color: $color-dark-orange;
            color: $color-dark-orange;

            &:hover:enabled,
            &:focus:enabled,
            &:visited:hover,
            &:link:hover {
                background-color: $color-dark-orange-outline;
            }
        }

        &:hover:enabled,
        &:focus:enabled,
        &:visited:hover,
        &:link:hover {
            background-color: $color-dark-orange-hover;
        }
    }

    &--green,
    &--green:visited {
        background-color: $color-green;

        &.btn--outlined {
            border-color: $color-green;
            color: $color-green;

            &:hover:enabled,
            &:focus:enabled,
            &:visited:hover,
            &:link:hover {
                background-color: $color-green-outline;
            }
        }

        &:hover:enabled,
        &:focus:enabled,
        &:visited:hover,
        &:link:hover {
            background-color: $color-green-hover;
        }
    }

    &--dark-green,
    &--dark-green:visited {
        background-color: $color-dark-green;

        &.btn--outlined {
            border-color: $color-dark-green;
            color: $color-dark-green;

            &:hover:enabled,
            &:focus:enabled,
            &:visited:hover,
            &:link:hover {
                background-color: $color-dark-green-outline;
            }
        }

        &:hover:enabled,
        &:focus:enabled,
        &:visited:hover,
        &:link:hover {
            background-color: $color-dark-green-hover;
        }
    }

    &--red,
    &--red:visited {
        background-color: $color-red;

        &.btn--outlined {
            border-color: $color-red;
            color: $color-red;

            &:hover:enabled,
            &:focus:enabled,
            &:visited:hover,
            &:link:hover {
                background-color: $color-red-outline;
            }
        }

        &:hover:enabled,
        &:focus:enabled,
        &:visited:hover,
        &:link:hover {
            background-color: $color-red-hover;
        }
    }

    &--outlined {
        border: 1px solid;
        box-sizing: border-box;
        background-color: $color-white;

        &.btn--small {
            padding-left: 15px;
            padding-right: 15px;
        }

        &.btn--regular,
        &.btn--large {
            padding-left: 23px;
            padding-right: 23px;
        }
    }

    &--block {
        display: block;
        width: 100%;
    }

    &:disabled {
        opacity: 0.4;
        cursor: auto;
    }
}
</style>
